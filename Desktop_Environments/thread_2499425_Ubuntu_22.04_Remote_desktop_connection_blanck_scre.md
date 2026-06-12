---
title: "Ubuntu 22.04 Remote desktop connection blanck screen (eGpu installed)"
date: 2024-07-26
forum: Desktop Environments
---

### Post by hakan439 on 2024-07-26
Hi, I installed Ubuntu on my mini desktop machine and connected eGpu for ai-related work for my Phd thesis. But I can not connect to machine via remote desktop. Setting up Cuda engine and drivers were very problematic but at the end they are working. But I can not remote connect to machine.  

I am not logged in locally and tried bunch of solutions on the web but did not succeed.

---

### Post by currentshaft on 2024-07-26
> **hakan439 said:**
> Hi, I installed Ubuntu on my mini desktop machine and connected eGpu for ai-related work for my Phd thesis. But I can not connect to machine via remote desktop. Setting up Cuda engine and drivers were very problematic but at the end they are working. But I can not remote connect to machine.  

I am not logged in locally and tried bunch of solutions on the web but did not succeed.

What does "can not connect" mean? We're not mind readers and we're not in front of your computer.

What "bunch of solutions" did you try?

---

### Post by ActionParsnip on 2024-07-26
When you do your AI work...how do you do it? In a terminal? A web browser? There may be a sleeker solution to what you want to do

---

### Post by hakan439 on 2024-07-26
Yes you are right, I gave no details. 
I have 3 computers in my LAN, One is for db, one is for my simulations and the last one is this ubuntu desktop with egpu installed for deep learning trials. 
I write python code in Pycharm. Normally, I normally connect these machine remotely from my laptop and work on them remotely. computers are located in another room with UPS attached. It is cramped and not very comfortable to work there, therefore I connect them remotely. 

I need to use desktop environment on ubuntu machine for DL development. Now I connect this pc to a tv on that room but it is very hard to work like that. I sometimes work hours in a very uncomfortable position. Therefore I need to solve remote connection problem. 
When I try to connect remotely, there is a blank screen with a cursor only. Nothing happens. Then xrdp window appears. I enabled remote connection and remote login from settings. I can connect via SSH from terminal. 


I haven't noted every method I tried. Last one was this. 
[https://answers.microsoft.com/en-us/windows/forum/all/remote-desktop-connection-shows-black-screen-when/a56a924a-3458-4fab-8229-7888058dd533](https://answers.microsoft.com/en-us/windows/forum/all/remote-desktop-connection-shows-black-screen-when/a56a924a-3458-4fab-8229-7888058dd533)
[https://help.ubuntu.com/community/xrdp](https://help.ubuntu.com/community/xrdp)

---

### Post by currentshaft on 2024-07-26
> **hakan439 said:**
> 
I need to use desktop environment on ubuntu machine for DL development. 

Why? What application are you trying to use?

---

### Post by hakan439 on 2024-07-26
> **currentshaft said:**
> Why? What application are you trying to use?

Mainly Pycharm.

---

### Post by currentshaft on 2024-07-26
You could run Pycharm locally and access the remote files with sshfs:

mkdir remote
sshfs <remote desktop>  remote

Or you could use Pycharm remotely over SSH, it will be much slower though:

ssh -Y <remote desktop> -t pycharm

---

### Post by TheFu on 2024-07-26
+1 for using remote ssh with X11Forwarding to run remote programs.

Of course, this assumes your local workstation runs an X/Server.
```
$ ssh -X userid@remote-IP-or-hostname  "command to be run with options"
```

If the command run on the remote computer is a terminal, you can launch any GUI program from that and any number of GUI programs from the same terminal.  Of course, lots of GUI programs, mainly from Gnome, will spew crap all over the screen because they can't be bothered to support debugging levels and have no output when everything is fine (or not an error).

This way, the remote program fully integrates into your local desktop. The window looks like any other local window. Perhaps the titlebar says the remote system name, if you have it configured to do that.

Remote desktops are so, so, so, MS-Windows.  Unix and Linux haven't needed them since around the mid-1980s with X/Windows.  There are times, when, for security reasons, you may not want to have any data locally on your computer - like when you are traveling - so having a remote desktop back to your home country and home workstation(s) may be more desirable.  That way when the evil maid comes and steals everything on your HDD, she gets just a remote desktop program, but not the unlocked credentials or certs needed to access the remote system.

I don't know if Wayland works the same way for all applications or not. I hope it does, but I've not tried Wayland in a few years.

---

