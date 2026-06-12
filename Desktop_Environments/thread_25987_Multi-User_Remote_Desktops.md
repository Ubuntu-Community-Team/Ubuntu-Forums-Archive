---
title: "Multi-User Remote Desktops"
date: 2005-04-11
forum: Desktop Environments
---

### Post by sundialsc on 2005-04-11
I noticed the cool new feature in Gnome that lets you enable Remote Desktop just like XP.  Very cool.

My question:  Can this be setup so you do not have to be logged in as a user?  I want to use it as a Linux type terminal server if possible.

By the way what an awesome distro.  Fedora was getting me at my wits end.

Sundial

---

### Post by cwaldbieser on 2005-04-12
I think I understand what you mean, but there is still some room for ambiguity.  If you want to know if it is possible to have an Ubuntu server with no one logged in initially, and then several users can log in with remote desktop clients and start their own sessions, the answer is "sort-of".

Both Gnome and KDE use the RFB (remote frame buffer) protocol to share the desktop.  In KDE, the program is called krfb, and in Gnome, it is called vino.  Both are really flavors of VNC (virtual network computing), which is kind of like a remote control for your computer.

VNC programs are composed of 2 parts-- a client and a server.  VNC clients and servers exist for Windows, Macs, and Linux.  Since the RFB protocol is open, they can all be used compatibly (e.g. a Windows client can control a Mac server, a Mac client could control a Windows server, ...).

VNC doesn't start a new session, though, so as you pointed out, a user must be logged on and running the VNC server for the client to remote control.  However, because of the way the X Display server works, there are versions of VNC servers for Linux that actually do give multi-session like behavior.

The way these multi-session servers work is by creating fake X display sessions that VNC clients remote control, so no atual user's desktop is being controlled.  The resulting behavior is much like a Windows terminal server.

There is even more to this story, though!  The X Display server works across networks, so Linux-Linux connections don't need any special programs.  There are some security issues going this route, but a simple way to overcome security problems is to use X with ssh.

If you issue a command like:

```
$ ssh -Y -l myusername hostname
```

You will get a console login to the machine called hostname.  However, once you are logged in, if you issue a command like:

```
$ gedit myfile.txt
```

The graphical gedit application will appear on your local display and allow you to edit the file, myfile.txt, on the remote server!  The way this works is the -Y option in the ssh command tells ssh to forward all X display commands back to your local X display server.

There is a program out now called FreeNX that combines some of these ideas (X display sharing, encryption, data compression) and makes the whole experience like a turbo charged terminal server that performs well even over a very slow connection (like dial-up).  I find that it is a little difficult to set up right now, but I expect that as time goes on, the setup will become easier.

Hope my rambling helped answer your question!

---

