---
title: "Bf2CC, mono, bf2 and pr"
date: 2010-10-27
forum: Gaming &amp; Leisure
---

### Post by alexblodøks on 2010-10-27
Hello. I am in the process off setting up a dedicated server for bf2. However, im running into some issues, trying to install bf2cc and mono.

As i understand, i have to use mono 1.1.12.

I made a new user "bf2server" and put server and mono files there. I ran the server file sucessfully, but the mono files are giving me a headache.

I run these commands after downloading the mono files.

chmod +x mono-1.1.12.1_0-installer.bin
./mono-1.1.12.1_0-installer.bin

But after the last command nothing happens?
I also tried downloading the source codes but when i run

tar xzf mono-1.1.12.tar.gz

[FONT=Verdana]I just get alot of cannot open: no such file or directory.[/FONT]

[FONT=Verdana]We are running ubuntu 10.10, from I3d. I read on another forum, someone had the same problem, and I3d advised him to only install 4 packages[/FONT].
[FONT=Verdana]namely: mono-core, -data, -web and -winforms[/FONT]

[FONT=Verdana]I am very new to linux so any help on how to solve this would be much appreciated.
[/FONT]

---

### Post by ELD on 2010-10-27
At what step do you get "[FONT=Verdana]I just get alot of cannot open: no such file or directory."

That means whatever your trying to do the item doesn't exist. You need to "cd" into the directory the files are in to run them.

so "cd /home/username/Downloads/"
then "[/FONT]./mono-1.1.12.1_0-installer.bin" for example.

---

### Post by alexblodøks on 2010-10-27
The mono files are in /home/bf2server/bf2/mono.

I run command:

bf2server@server3212:~$ cd /home/bf2server/bf2/mono
bf2server@server3212:~/bf2/mono$ ls
libgdiplus-1.1.11.tar.gz  mono-1.1.12_0-installer.bin  mono-1.1.12.tar.gz  mono-1.2.5.1_3-installer.bin

I then run  

bf2server@server3212:~/bf2/mono$ tar xzf mono-1.1.12.tar.gz

then i get a long list like this

tar: mono-1.1.12/mcs/gmcs/typemanager.cs: Cannot open: No such file or directory
tar: mono-1.1.12/mcs/gmcs/symbolwriter.cs: Cannot open: No such file or directory
tar: mono-1.1.12/mcs/gmcs/tree.cs: Cannot open: No such file or directory
tar: Exiting with failure status due to previous errors

Same thing for the bin file.

bf2server@server3212:~/bf2/mono$ sudo chmod +x mono-1.1.12_0-installer.bin
bf2server@server3212:~/bf2/mono$ ./mono-1.1.12_0-installer.bin
bf2server@server3212:~/bf2/mono$

I have 10.10 on a local machine, i tried doing the same thing thre, and managed to install the mono files, however, when i tried running
$ mono bf2ccd.exe i got some message that mono wasnt installed.

---

### Post by directhex on 2010-10-27
You don't need to use Mono 1.1.12

And you'll likely bake your system trying to install it.

---

### Post by alexblodøks on 2010-10-27
How do i run bf2ccd.exe if i dont need mono?

as i said, i managed to install mono on my local computer, but when i run bf2ccd.exe i get:

 [FONT=&quot]charlott@ubuntu:/home/bf2server/bf2$ sudo mono bf2ccd.exe[sudo] password for charlott: 

** (bf2ccd.exe:3892): WARNING **: The following assembly referenced from /home/bf2server/bf2/bf2ccd.exe could not be loaded:
     Assembly:   System.Runtime.Remoting    (assemblyref_index=7)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bf2server/bf2/).


** (bf2ccd.exe:3892): WARNING **: Could not load file or assembly 'System.Runtime.Remoting, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Runtime.Remoting, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: "System.Runtime.Remoting, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"[/FONT]

---

