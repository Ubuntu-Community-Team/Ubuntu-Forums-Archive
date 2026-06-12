---
title: "Remote Desktop"
date: 2005-08-01
forum: Desktop Environments
---

### Post by DrQuincy on 2005-08-01
Hi  I have an XP machine and a Kbuntu machine that both connect to the Internet through a router.  I want to be able to do remote desktop from one to the other but can't figure out where to start - can anyone point me in the right direction?

---

### Post by cwaldbieser on 2005-08-01
[QUOTE=DrQuincy]Hi  I have an XP machine and a Kbuntu machine that both connect to the Internet through a router.  I want to be able to do remote desktop from one to the other but can't figure out where to start - can anyone point me in the right direction?[/QUOTE]

Do you have XP Pro or XP home?  I am not 100% sure, but I don't think XP Home can act as a terminal server.  Also, I think XP Pro only supports one connection at a time.

You would probably be better off installing [tightvnc](http://www.tightvnc.com/)  on the XP box.  It is like a remote control for the box (rather than starting a new session).  You can also get VNC clients/servers from the repositories for your Kubuntu box (Ubuntu has vino installed by default, I think).  For Kubuntu, I just use vncserver when I'm in the mood.  

Most of the time, I just use ssh to connect to my Kubuntu box-- you need to get sshd from the repositories and PuTTY or some other ssh client for Windows.  The upside is that it is very easy to use and is pretty quick.  Some people shy away from the command line, though.

If you want to remote desktop from Kubuntu to a Windows box that supports it, you can use "krdc" or "rdesktop".  It doesn't work in reverse, though (no rdp server for Kubuntu).  

If you want to try remote X-Sessions, you need to get an X Server running on Windows.  This is possible through commercial packages, Cygwin, TopologiLinux, etc.

---

### Post by mbeach on 2005-08-10
I'm going to jump in here and ask if the remote desktop allows reverse connections (similar to windows 'add new client' to a listening viewer).  I've read that there is a helper app for vncserver called vncconnect but I can't seem to locate a copy - any pointers before I spend a morning looking for the impossible (which will keep my completely content for a day).

tia,
mb

---

