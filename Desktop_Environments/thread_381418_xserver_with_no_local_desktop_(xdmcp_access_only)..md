---
title: "xserver with no local desktop (xdmcp access only). Can it be done?"
date: 2007-03-10
forum: Desktop Environments
---

### Post by belboz on 2007-03-10
I searched a bit and couldn't see if this was possible or not, so here is my question.

Is it possible to onlu run a desktop manager on a box that only allows xdmcp connections to it with no actual GUI running on the box itself?

The above description is probably confusing (it is for me!) so I will try to describe the setup for the above.

I have a box running a server install of xubuntu.  I don't have any X server running on it (no gdm, no desktop managers yet,etc).  It is basically a command line box running a bare minimum setup.  I am using it as a file server (samba) for a bunch of systems on my network.  (OS X and XP boxes).   I am also running ccxstream on it so it allows my xbox to view videos stored on it.

It is a fairly beefy box, but I have it in a closet with another linux box running smoothwall.  

Anyway this file server has no keyboard, mouse, or monitor plugged into it.   I access it currently with ssh.

I would like to have access to KDE/XFCE/GNOME from my main desktop PC in my study (a dual powermac g5).  Supposedly I can run Apples X11 client and connect to remote desktop managers running xdmcp and run applications off that box.

I am curious if it is possible to run gdm and desktop manager(s) on the Linux box, but not have it worry about  running the actual xserver on the Linux box?  Just allow remote connections from other computers over XDMCP. 

Not concerned about speed on the clients.  Just looking to be able to run some Linux X11 apps on the G5 with XDMCP to play with some of the various desktops available on Linux.

I just don't have the room in the study to put a second box running Linux, and I don't want to run Ubuntu on the G5 itself.

Is this possible and any advice or links on how to make something like this happen?  I am assuming i need to install gdm and have it only look for remote connections, and not try to access a local x server or do any graphical setup on the local linux box or try to communicate with the mouse,etc.

---

### Post by belboz on 2007-03-11
Any thoughts?

---

### Post by enopepsoo on 2007-03-11
did you try vnc?

---

### Post by belboz on 2007-03-11
Not sure I follow how VNC would work in this situation.

From what I understand under a normal Ubuntu installation you have the following setup.

GDM Desktop Manager running
xorg xserver running.
And then whatever desktop your using (KDE, Gnome, XFCE, Fluxbox etc).

So when you boot the system the xserver starts up and gdm comes up letting you log in under your desktop of choice.

Now what I want to do is not run xorg or any xserver on the Ubuntu box.  I want GDM to run but don't want the Ubuntu box to fire up any graphical environment on it at all.  I want to keep the Ubuntu box console only.

Then have an xserver running on a separate client (be it a Mac, Linux box, or even Windows machine).  Have it connect to GDM on the Ubuntu box and let you log in and run the desktop of your choice.

I believe this is how many thin clients setups work.

My problem is I am not sure how I would go about installing gdm and the various desktops (KDE,Gnome, Xfce, and Fluxbox) without an xserver getting loaded and activated also.

Looks like doing an apt-get install of gdm doesn't force any installation of xorg, so I assume this would be the first stepping point.   Get gdm installed and have it wait for connections from remote xservers.  Not sure on the specifics for doing this.

Then I think I need to install the various desktops I want, but somehow hold back the xserver from getting installed.

---

### Post by skiy on 2007-06-01
Hi

I'm running Ubuntu Feisty 7.04 amd64

1) Dont worry about whether or not you have installed xserver-xorg or not! It makes no difference.
2) Do a apt-get install gdm
3) Do a apt-get install xvfb
4) nano -w /etc/gdm/gdm.conf
Replace all instances of
/usr/X11R6/bin/X
with
/usr/bin/Xvfb

Also, under the XDMCP section, change
Enable=false
to 
Enable=true

(4.5)*UPDATE*
This fixes a bug about unknown "vt7" parameter:
nano -w /etc/gdm/gdm.conf
Replace 
VTAllocation=true
with
VTAllocation=false

5) /etc/init.d/gdm restart
6) From a DIFFERENT computer do XWin -query yourserver

A login screen should now be displayed.

---

### Post by skiy on 2007-06-03
Unfortunately, while the Xvfb solution I posted worked for me the first time, in subsequent /etc/init.d/gdm starts I get an "X server keeps crashing window" saying that the binary "X" was passed an invalid parameter "vt7" this happens 4 out of 5 times when i start gdm. 1 in 5 just works. Very strange 	
:confused:

*this is fixed in above post*

---

### Post by jackocleebrown on 2007-06-03
What about using Nomachine NX instead of xdmcp? Should be much faster. I've got a server at work that just sits runs as console and users connect to it using NXclient with a full gnome desktop. I must admit though that I do have Xserver installed (but not running), I'm not sure if it is required for NX or not. Plus you can connect from windows boxes if you need to. [www.nomachine.com](www.nomachine.com)
Jack

---

### Post by bkortleven on 2007-08-22
We are trying to get a similar situation running:

headless/X-less machine with Ubuntu Server 6.06 installed, and a virtual chrooted Ubuntu Desktop 7.04 installation. This because we need to run some default server things on the same machine.
Several Igel X-thinclients are connecting to this machine (through XDMCP).

I get the gdm (in the chrooted) running, and the ThinClients are connecting and running (apart from some issues like 'remote' sound etc...)
BUT
the local X session still tries to start, which isn't configured and wanted.

I tried disabling and editing all parameters in gdm.conf (on the 'virtual's location), but to no resolution...

Anyone any idea?
Please let me know!

---

### Post by bkortleven on 2007-11-27
We changed our setup a little bit.

The chrooted setup of the Feisty installation was redone in VMWare, just a full install. We had a little too much dependent and errornous  librarie things that were causing us a major headache.

VMWare server was installed, gdm.conf was adjusted and the server runs/accepts XDMCP...

The three Igel thinclients run fine now...
Three people working on them constantly, no major issues...
Now a fourth computer was added to the setup: an Ubuntu Feisty Desktop installation on a portable, and the user can do a 'Remote Login' on the login page...

If anyone needs more info about this setup: just let me know ;)

---

