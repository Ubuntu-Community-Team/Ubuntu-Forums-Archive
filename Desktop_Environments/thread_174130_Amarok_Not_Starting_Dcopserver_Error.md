---
title: "Amarok Not Starting Dcopserver Error"
date: 2006-05-11
forum: Desktop Environments
---

### Post by TheWind on 2006-05-11
Hi to all of you, 
I have a problem with Amarok. Today i made an installation from the Synaptic manager of this Audio Player, but after that every time i open the program it shows me several windows with different errors, especially refering to this Dcopserver, asking if it is running. 
I have used Amarok before, but in this last reinstall of Ubuntu 5.10 no way. ](*,) 
I was looking on Internet the whole day for a solution but i didn't find it. At the end of the Thread there are three Snapshots of my desktop while opening Amarok so you can see the errors that appeare to me. Also here i'm giving you what is the code coming out of the terminal when i launch Amrok from there. 
Hope Someone could help me fix this. I was wondering maybe the firewall is blocking Amarok or as i have an wireless Wpa secured connection this may be the reason. I don't know. I did several installs and uninstalls but even that didn't worked. And if it's usefull i'm running Gnome Desktop. I like this player so i would be happy to use it again. And as it seems is one of the best under Linux. So Any suggestions?
Here is the Code: ```
dimo@ubuntu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
trying to create local folder /home/dimo/.kde/share: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/dimo/.kde/socket-ubuntu/kdeinit__0'
DCOPClient::attachInternal. Attach failed Could not open network socket
dimo@ubuntu:~$ trying to create local folder /home/dimo/.kde/share: Permission d enied
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/dimo/.kde/socket-ubuntu/kdeinit__0'
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
KTempFile: Error trying to create /home/dimo/.kde/socket-ubuntu/amarokXXXXXX.sla ve-socket: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
amarok: ERROR: : couldn't create slave : Unable to create io-slave: Permission d enied
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype amaroK/Plugin not f ound
kio (KMimeType): WARNING: KServiceType::offers : servicetype amaroK/Plugin not f ound
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
trying to create local folder /home/dimo/.kde/share: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
trying to create local folder /home/dimo/.kde/share: Permission denied
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
DCOPClient::attachInternal. Attach failed Could not open network socket
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/socket-ubuntu: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/dimo/.kde/socket-ubuntu/kdeinit__0'
dimo@ubuntu:~$ DCOPClient::attachInternal. Attach failed Could not open network socket
There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running!
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/dimo/.kde/cache-ubuntu: Permission denied
kbuildsycoca: ERROR creating database '/home/dimo/.kde/cache-ubuntu/ksycoca'!
kbuildsycoca: Wrong permissions on directory? Disk full?



```
Thank you]:-k

---

### Post by louis_nichols on 2006-05-11
I think this line

trying to create local folder /home/dimo/.kde/share: Permission denied

is the key. What is the output when issuing in terminal the command:

```
ls -lah ~ | grep kde 
```

---

### Post by TheWind on 2006-05-11
Thank you Louis Nichols for the replay,
So here is what i got if i type in the Terminal that command:

```
dimo@ubuntu:~$ ls -lah ~ | grep kde
drwx------   3 root root 4,0K 2006-04-21 13:09 .kde
dimo@ubuntu:~$                                                
```
What do you think?

---

### Post by TheWind on 2006-05-11
Finally i got the solution it was a permissions issue solved by a command that i find in this thread:[http://www.ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver]("http://www.ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver") 
Thank you guys!:D

---

### Post by louis_nichols on 2006-05-11
yeah, that was the idea. as you can see in the output, the owner of those files was root, so you couldn't write to it.

i didn't visit that thread, but i believe you used command chown (and maybe chmod) to solve the issue.

---

### Post by TheWind on 2006-05-11
Yep, I used that command chown......i'm step by step getting to know more of this system...but thank you for your help again.
:D :D

---

### Post by louis_nichols on 2006-05-11
wellcome! :) glad it works.

One tip: try not starting GUI apps using sudo (it's what caused your issue). Use kdesu or gksudo instead. Or the option to run an app as another user, which is in the Applications menu, under system tools.

---

