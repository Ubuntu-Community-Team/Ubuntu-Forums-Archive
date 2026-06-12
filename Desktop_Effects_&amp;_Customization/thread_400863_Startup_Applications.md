---
title: "Startup Applications"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by Gabina on 2007-04-04
I hope I'm in the right forum.  I'm a newbie to Linux.

I want Remote Desktop to start automatically when I log in.  Is there a way to do that? I found the Startup Applications, but it needs commands, and being a newbie, I don't know what the command is for Remote Desktop to activate.  Since I do most computing from my work office, I need remote access to compute on this computer. 

Any help out there? 

Thanks.

--Gabrielle

---

### Post by Monster_user on 2007-04-04
This link provides some information on setting up vncviewer. The Remote Desktop client of choice for Ubuntu.

[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)


This would be a command to connect to a remote desktop system.

vncviewer -fullscreen 192.168.1.x:0

Type "man vncviewer" to view the MAN, or Manual pages for VNC Viewer. It should list more options.

---

### Post by Gabina on 2007-04-04
Thanks, but it's not quite what I need.  

I want to let any other computer (Windows computers) to be able to remotely connect to my Ubuntu computer.  Presently, by the GUI in Remote Desktop, I'd have to activate it and enter the password I'd want for remote access each time after I log in. 

I want to leave the Remote Desktop server open.  I do that on my Windows machines by making it a service. It starts even before I log in. Thus, when I go to work (WindowsXP), I can remotely connect to one home computer (WindowsXP) through VNC and from there get into any of my others either by VNC or Remote Desktop Connection in Windows.  What I can't do is get to this Ubuntu computer, unless I've sat at this desk and activated Remote Desktop after logging in.

I'd rather it just be activated (as a server) automatically after I log in.  The Start Programs need the command and I don't know what the command is.  The one you offered was to view another computer.  I want to be able to view this one from another computer. 

Can you give me the command for that?  I'm getting a feeling it has something to do with vino-server.

Thanks.

--Gabrielle

---

### Post by Monster_user on 2007-04-09
Sorry, I haven't used a remote desktop application before. It is 'vino-server'.

I dropped it into Google, and this thread came up.

[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

---

### Post by komputes on 2007-12-17
I would like to automate the VNC server starting at the login window, as well as an automatic-no-password-to-enter-no-hassle VNC connection as well, so I'm guessing I would need to make a shell script sing the RDP client doesn't allow me to save the connection with a password. I also have a few shell scripts that I want to run at start-up, but I'm not sure which file to edit.

I was reading the documentation on "vncviewer" and there is a part that I am interested. How should I configure the password file for VNC? Is it just a plaintext file with the password or is there one line with each server address and the associated password. 

       -passwd password-file
              If  you  are on a filesystem which gives you access to the pass&#8208;
              word file used by the server, you can specify it here  to  avoid
              typing it in.  It will usually be "~/.vnc/passwd".

Thanks to anyone who has automated their VNC connection or at least added a few start-up scripts.

---

