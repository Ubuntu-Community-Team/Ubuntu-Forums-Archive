---
title: "SSH X Session"
date: 2006-06-27
forum: Desktop Environments
---

### Post by lochok on 2006-06-27
Good Afternoon

I've got a laptop running a default installation of Ubuntu, with many extra utilities and programs includiing the SSH Server. I also have a desktop running WinXP, PuTTY and Xming with which I can connect to the laptop and use it as a console, but I can't tunnel X Sessions across to the desktop.

I have added
X11Forwarding yes
to /etc/ssh/sshd_config and /etc/ssh/ssh_config but whenever I try to connect I either get xterm Xt error: Can't open display: localhost:10.0
or
Xlib: connection to "localhost:11.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
xterm Xt error: Can't open display: localhost:11.0

Any help anybody? I'm not sure even if my x-server on this pc is doing what it's supposed to


Lachlan

---

### Post by craig552 on 2006-06-27
Try using the -X option:

[FONT="Courier New"]ssh -X user@computer[/FONT]

---

### Post by lochok on 2006-06-27
I get this as a response:

/usr/bin/xauth:  error in locking authority file /home/lachlan/.Xauthority
Error: Can't open display: localhost:10.0

---

### Post by lochok on 2006-06-27
Slightly different error now. When I type xterm & I get the following:
 X connection to localhost:10.0 broken (explicit kill or server shutdown).
Any ideas?

---

### Post by TFleck on 2006-06-28
Im having the same problem here.
How do I start an X sessien with ssh?

---

### Post by harisund on 2006-06-28
First, make sure you have some X-server running on your Windows box. I use and have fallen in love with Cygwin, but if you prefer Putty+Xming that's fine. 

Then in putty , go to Connection->SSH->X11 in the left hand colomn, tick "Enable X11 forwarding" and in the X display location textbox enter 127.0.0.1

Make sure your Xming is running and now establish ocnnection using putty and report back :)

---

### Post by Aelfric5578 on 2006-07-07
I'm having the same problem as the original poster.  I followed the steps outlined above, and now when I try to run an application I get:
```
guest@thorin:~$ xterm
xterm Xt error: Can't open display: thorin:10.0

```

Also, I only get this error if I log in under this seldom used guest account.  If I use any other login, I still get the original "wrong authentication protocol" error.

---

### Post by TFleck on 2006-07-10
> **Aelfric5578 said:**
> I'm having the same problem as the original poster.  I followed the steps outlined above, and now when I try to run an application I get:
```
guest@thorin:~$ xterm
xterm Xt error: Can't open display: thorin:10.0

```

Also, I only get this error if I log in under this seldom used guest account.  If I use any other login, I still get the original "wrong authentication protocol" error.

Are you using the -X option when starting ssh? "ssh -X <ip>"

---

### Post by Aelfric5578 on 2006-07-10
I was using PuTTY and Xming so I don't think the -X option applied to me, but I did check the "Enable X11 forwarding" box.  Although, seeing your post and the one above mine I decided to try using Cygwin.  Even with "ssh -X user@host" I get the same error: "Can't open display: thorin:10.0"  And if I try to open anything other than xterm, I get "Can't open display: (null)"

What am I doing wrong?

---

### Post by harisund on 2006-07-10
Ok here's the deal. Whether you are using Cygwin or Putty (I haven't used Xming, so I don't know) you need to first start your X server in the background. That is what "draws" the applications on screen. 

Putty doesn't come with a X server. Neither does Cygwin (by default). If you are running Cygwin, I am assuming you installed it yourself. Open up setup.exe, and make sure that the X11 packages are installed (only a few need to be installed. Look up documentation for Cygwin/X)
[http://x.cygwin.com/docs/ug/setup-cygwin-x-installing.html](http://x.cygwin.com/docs/ug/setup-cygwin-x-installing.html)

Then start the X server 
[http://x.cygwin.com/docs/ug/using.html](http://x.cygwin.com/docs/ug/using.html)

When you do this you will find a small X icon on your system tray, next to the calendar, volume control and others if you have any. That means your X server is running. Without this, neitehr Cygwin nor Putty will be of any help. 

If you are using Putty and Xming, I am assuming Xming sets up the X server for you. Assuming that my assumption is true (;)) check the enable X11 forwarding box and type in 127.0.0.1

And no, you don't particularly need X term. All you need is a X server running the background.

---

### Post by Aelfric5578 on 2006-07-10
I've checked my installation of Cygwin, I did have Cygwin/X installed.  I even updated everything to the latest version to be sure.  Now, if I try to connect using "ssh -X user@computer" I get that second error that **lochok** was getting: "X connection to thorin:10.0 broken (explicit kill or server shutdown)."  

I also checked my installation of Xming.  I can run the X applications that I think came with Cygwin/X using either Cygwin or Xming.

But if I try to connect to my remote Ubuntu machine using PuTTY, with Xming open, enabling X11 forwarding and typing in 127.0.0.1, I still get either "Can't open display: thorin:10.0" or "Can't open display: (null)."

(Both of those errors come when I try to run an application, not when I'm logging in)

As far as the xterm thing goes, that was just the simplest X application I could think of to test if X forwarding had indeed worked.  I've since tried xclock, nautilus, and several other programs as well, with the same results.

---

### Post by lebm on 2007-07-10
I have the same problem.
PuTTY+Xming trying to tunnel X11 when accessing a Linux/Unix box.
The problem started when I did an upgrade to Xming 6.9.0.24.
Until Xming version 6.9.0.23 all my X11 tunnel with Linux, Solaris and AIX worked.
Maybe Xming 6.9.0.24 has same new configuration that needs to be adjusted.

---

### Post by lebm on 2007-07-10
Well, as I suspected, something changed with Xming that affected all my PuTTY+X11 tunnels.
I removed Xming 6.9.0.24 and installed back Xming 6.9.0.23, now all tunnels are working.

---

### Post by SIZABANTU on 2007-09-14
I kind of had the some issue this worked for me.

$vim /etc/hosts

edit first line to reflect lo address. The syntax is different than the other addresses:
127.0.0.1 localhost

Make sure you leave the other addresses alone.
see: man hosts for further info

I found the solution here [http://www.linuxquestions.org/questions/showthread.php?threadid=57384](http://www.linuxquestions.org/questions/showthread.php?threadid=57384)

Finally fixed :popcorn:

---

