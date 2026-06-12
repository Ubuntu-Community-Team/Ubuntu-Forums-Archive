---
title: "Use ssh X  forwarding on vanilla ubuntu desktop install?"
date: 2009-08-10
forum: Desktop Environments
---

### Post by SoftwareExplorer on 2009-08-10
I want to be able to login to my computer graphically when someone else is it the physical computer and to be able to use it without getting in each others way. I've tried to read up on ssh X forwarding, but I can't seem to get it. I would like to be able to not interrupt the normal X on both computers if that's possible. To that end, I've tried to use xepher, but couldn't figure out how to fit the pieces together. Thanks in advance, I've read so many tutorials that didn't work and I'm ready for some two-way help.

---

### Post by SoftwareExplorer on 2009-08-13
From what I've read, it should be easy. but I'm not getting something basic right or something.

---

### Post by fela on 2009-08-22
Just run on the client:

```
ssh -X user@server
```

Enter your password and run any program you like, graphical or not. That includes the gnome panel, metacity, compiz, whatever. Tip: if you don't need compression (I think it's that) you can use -Y instead of -X.

---

### Post by SoftwareExplorer on 2009-08-22
> **fela said:**
> Just run on the client:

```
ssh -X user@server
```Enter your password and run any program you like, graphical or not. That includes the gnome panel, metacity, compiz, whatever. Tip: if you don't need compression (I think it's that) you can use -Y instead of -X.
Thanks for the help. It gives me this ```
ssh bjorn-backup
bjorn@bjorn-backup's password: 
Linux bjorn-backup 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Aug 15 22:43:13 2009 from 192.168.0.120
bjorn@bjorn-backup:~$ exit
logout
Connection to bjorn-backup closed.
bjorn@bjorn-desktop:~$ ssh -X bjorn@bjorn-laptop
bjorn@bjorn-laptop's password: 
Linux bjorn-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

*** System restart required ***
Last login: Tue Aug 18 21:12:20 2009 from bjorn-desktop.local
/usr/bin/X11/xauth:  /home/bjorn/.Xauthority not writable, changes will be ignored
bjorn@bjorn-laptop:~$ gedit
X11 connection rejected because of wrong authentication.

(gedit:13896): Gtk-WARNING **: cannot open display: localhost:10.0
bjorn@bjorn-laptop:~$ 

```
Do you know what I'm doing wrong? I'm already running X on both of them (thats what I meant when I said vanilla ubuntu installs) when I run the command, is that a problem?

---

### Post by arch0njw on 2009-08-22
Have you tried xhost+ on the machine your ssh'ing from?

---

### Post by fela on 2009-08-22
I'm sure the .Xauthority thing must mean something. Also, it says you need to reboot. Why don't you try that first? ;)

---

### Post by SoftwareExplorer on 2009-08-23
Tried rebooting. Can't seem to figure out the Xauthority thing. 

How would I use xhost. 

PS:When you explain, can you make clear the difference of steps to do on the server and on the client?

---

### Post by hl2040 on 2009-08-23
I am having the same problem. I have X installed on two Ubuntu 8.04 machines, and I get the same Gtk error complaining about being unable to open the display. That message is not surprising in a way because when I ssh in using ```
ssh -X host@remote
```, the DISPLAY environment variable does not even exist! When I ssh to a Debian testing machine I have access to with -X, DISPLAY is set as it should be, and X forwarding works fine, and I can launch xterm and gedit just fine.

I have also checked the /etc/ssh/sshd_config and /etc/ssh/ssh_config ssh client and server config files on both ubuntu machines and all have X11 forwarding enabled. What gives?

---

### Post by hl2040 on 2009-08-23
Fixed it! Just install the xauth package.

The solution is revealed upon reading /usr/share/doc/ssh/README.Debian.gz under the section "X11 Forwarding". You just need to install the 'xauth' package - this could be a dependency of ssh, but since X11 forwarding is turned off by default now, xauth is only a "Suggested" dependency of ssh, but is a required dependency of xorg.

So in summary:
1. ensure the remote machine's /etc/ssh/sshd_config file has the line "ForwardX11 yes"
2. Install xauth on the remote machine
3. install the X apps on the remote machine that you wish to run
4. Enjoy...

One way to also test if things are working is to install x11-apps. It comes with basic programs for testing the forwarding like xclock and xeyes.

---

### Post by SoftwareExplorer on 2009-08-23
I don't know if this is safe, but I tried removing ~/.Xauthority ~/.Xauthority-c ~/.Xauthority-l on both of the machines. I restarted the server and it worked. However GTK programs are ugly except for gnome-appearance-preferences. gnome-terminal gave me ```
Failed to contact the GConf daemon; exiting.
``` What does that mean?

---

### Post by SoftwareExplorer on 2009-08-23
As far as what hl2040 was saying, I already had xauth because Xorg is installed on both machines. My questions now are more out of curiosity, not necessity.

---

### Post by hl2040 on 2009-08-23
When you say "login graphically" do you mean run standalone remote programs (which is the problem I was thinking of) or a complete remote X session (like a remote desktop) ?

As to gconf, maybe you don't have all the basic gnome dependencies installed. At least under ubuntu 8.04, the "libgconf2-4" package contains the gconfd daemon, do you have that package installed?

---

### Post by SoftwareExplorer on 2009-08-23
I meant a whole session but single programs works ok to.
I think you have to removing ~/.Xauthority ~/.Xauthority-c ~/.Xauthority-l on the server cause I ssh to a different server and X forwarding didn't work. Remove those files and rebooted and it did fine.

---

### Post by SoftwareExplorer on 2009-08-26
> **hl2040 said:**
> When you say "login graphically" do you mean run standalone remote programs (which is the problem I was thinking of) or a complete remote X session (like a remote desktop) ?

As to gconf, maybe you don't have all the basic gnome dependencies installed. At least under ubuntu 8.04, the "libgconf2-4" package contains the gconfd daemon, do you have that package installed?

Yes I have it installed. I don't want to insult you, but I said that both of these machines are ubuntu desktop installs. So I would expect them to work unless there is a caveat that I don't know about with -X sshing.

---

