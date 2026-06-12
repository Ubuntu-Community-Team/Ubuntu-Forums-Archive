---
title: "Can't connect to vino server"
date: 2009-11-11
forum: Desktop Environments
---

### Post by bullka on 2009-11-11
I have a default Ubuntu Desktop 9.10 installation. The probolem is:

I can't connect using vncviewer. Sometimes I can.. and seems that I can only when I'm logged in locally to Gnome desktop and Screen Saver is not running. If I'm not logged in - vncviewer gives me an error that it can't connect.

I tried restarting the server remotely through SSH. Didn't help.

What are my options to connect to Gnome GUI remotely? What can I check/do/configure/enable through SSH?

---

### Post by bullka on 2009-11-11
Hi,

I thound a thread how to control vino server remotely: [http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981) but it assumes that I need to be logged in:

--
CAVEAT: A user must already be logged into the desktop on the target machine for this to work
--

Any ideas?

---

### Post by Nicolas_VP on 2009-11-11
1. What is your Video card? If you have Nvidia G-force as I have, so you should disable visual effects in Preferences - > Desktop settings. 
2. You should be logged in (in Ubuntu) when you trying to connect to this machine, otherwise you will see blank screen.

---

### Post by bullka on 2009-11-11
> **Nicolas_VP said:**
> 1. What is your Video card? If you have Nvidia G-force as I have, so you should disable visual effects in Preferences - > Desktop settings. 
2. You should be logged in (in Ubuntu) when you trying to connect to this machine, otherwise you will see blank screen.

1. Visual effects are disabled. I am aware of that issue with visual effects. My card is ATI. Are you able to connect to Ubuntu desktop at all while you're not logged in locally?

2. I don't even see a black screen. Vncviewer doesn't connect at all. Check the attachment.

What else could I install and configure to my Ubuntu desktop remotely through SSH to be able to see GUI?

---

### Post by Nicolas_VP on 2009-11-11
When I need to connect to my desktop while I'm not loggin in I'm using x11vnc. To use it you need to disable (kill the proccess in ssh) and run x11vnc from command line. 
All the information you can take from here:
[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)
Please not that vino and x11vnc are using the same port for the remote connection. So you can't run them simultaneously.

---

### Post by bullka on 2009-11-11
> **Nicolas_VP said:**
> When I need to connect to my desktop while I'm not loggin in I'm using x11vnc. To use it you need to disable (kill the proccess in ssh) and run x11vnc from command line. 
All the information you can take from here:
[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)
Please not that vino and x11vnc are using the same port for the remote connection. So you can't run them simultaneously.

Thanks. I will try.

---
Just tested with my wife at home: when she was not logged - I couldn't connect. When she logged to Gnome - I was able to connect with vncviewer to Home desktop GUI.
But this is not acceptable at all.

So I will try a solution with x11vnc you suggested.

---

### Post by plum7500 on 2009-11-26
So did x11vnc  work for you as I am having the similar problem? I do get further and can log in but am getting the black screen.

---

