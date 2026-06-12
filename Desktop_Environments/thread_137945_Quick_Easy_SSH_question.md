---
title: "Quick Easy SSH question"
date: 2006-03-01
forum: Desktop Environments
---

### Post by aqualad on 2006-03-01
I've managed to ssh my brother's cpu in the next room through the network, but I know there's a way to actually see his gui through ssh or some kind of similar program.  A friend has helped me many times through it and I just wanted to find out what it was and how I can install it on my brother's comp (hopefully through an ssh session).

I found something called Cygwin, but I don't know if that's it or not.  Any help would be appreciated :)

---

### Post by ThreeE on 2006-03-01
Are both machines Ubuntu?  Are you inside a trusted network?  If so, using XDMCP is the easiest solution.  You enable it on both machines under System, Administration, Login Screen Setup, Security.  Select Enable XDMCP and Allow running XDMCP chooser from the login screen.  Logout.  Hit F10 on the login screen and select the target machine.  Login remotely.

DO NOT DO THIS OVER AN UNTRUSTED NETWORK.

Cygwin is used on Windows boxes.  It will only give you a standard ssh command line interface.

Your other option for non-Gnome, untrusted networks is VNC.

---

### Post by RAOF on 2006-03-01
You can run GUI programs on another computer over ssh by using "ssh -X user@remotemachine", and just starting the program from the command line.

To actually see his entire GUI, you'd want to set up VNC - I believe that running "vino" from the command line will get you to the Gnome VNC setup applet, or you'd find it somewhere in System->Administration->*something*.

Then you'd run "vncviewer" on the local machine to connect to his box.

---

### Post by ThreeE on 2006-03-01
RAOF is correct, but you will only see individual app windows using X this way.  You won't see the entire GUI/Desktop.  You'll need VNC for this.

---

### Post by aqualad on 2006-03-01
Thank you, gonna give it a shot :)

---

### Post by aqualad on 2006-03-01
Okay, when I try to connect to the VNC server from my computer I get my connection refused.  How can I get myself accepted?

Edit: vino did nothing, though there is vino-preferences that brings up a gnome config page, but I can't do anything, the terminal says: "Autentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed."

---

### Post by aqualad on 2006-03-01
I found a guide in the wiki that's almost perfect, but towards the end a command is issued that isn't recognized by the server in my case.  The command is:

```
vncserver :1
```

I've tried to access the vnc preferences page both by terminal and by gnome, but it won't allow to change any settings.  Any suggestions?

---

### Post by rich on 2006-03-01
I know it's obvious : have you installed vnc4server ? Although the viewer is (I think) part of a standard install the server isn't.



Rich

---

### Post by claes on 2006-03-01
[QUOTE=aqualad]I've managed to ssh my brother's cpu in the next room through the network, but I know there's a way to actually see his gui through ssh or some kind of similar program.  A friend has helped me many times through it and I just wanted to find out what it was and how I can install it on my brother's comp (hopefully through an ssh session).

I found something called Cygwin, but I don't know if that's it or not.  Any help would be appreciated :)[/QUOTE]

Easiest way is to use ssh -X user@server 
And then just start the gui program you want to run. The graphical output will be tunneled trough the ssh session.

Cygwin is an opensource project to port linux applications to windows. And they even have a port of X for windows in it.

Claes

---

