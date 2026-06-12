---
title: "VNC Server to act like a Windows VNC server"
date: 2006-06-08
forum: Desktop Environments
---

### Post by RedPenguin on 2006-06-08
As some of you probably know, when you install VNC on a Windows machine, it controls everything, you can even use the logon screen.

My question is, how can I make is so that, no matter who logs in or what GUI is loaded, you can still remote control the machine just like a Windows VNC server?

---

### Post by DarthMandeep on 2006-06-08
X11VNC lets you view and control the same screen that is shown on the servers monitor. Is that what you're looking for?

---

### Post by linuchsan on 2006-06-08
you have to configure an other display adapter. like :0 :1 :2 etc.

---

### Post by RedPenguin on 2006-06-08
Any way to autostart x11vnc at startup?

---

### Post by DarthMandeep on 2006-06-08
I know there's a way to set Gnome to start a program or service whenever it starts, but I'm not using Gnome so I can't recall the details.

I use SSH to login to the server and start x11vnc. That's useful because you can use SSH to encrypt the vnc connection and compress it for lower bandwidth links.

---

### Post by scxtt on 2006-06-08
this is a total guess, but what about adding (a symbolic link, perhaps?) to the run level [ /etc/rc*.d/ ] you wish for the service to start under, or /etc/init.d in general?

i'm more used to using /etc/init.d/*d to start/stop daemons, but couldn't this work the same way even tho vncserver isn't a daemon? ... there has to be some directory which contains startup scripts/binaries ...

just a thought ...

and x11vnc sounds a lot like vino (which is installed by default in gnome anyways) ...

---

### Post by MystaMax on 2006-06-20
I'm not exactly sure what you are looking for. What do you mean by Windows VNC server? It seems like you want to be able to login to your machine via a remote session (vnc). As oppose to just viewing a session. 

Check this tutorial here, and see if this is what you want to do

[http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

---

### Post by rlgoddard on 2006-07-08
> **MystaMax said:**
> I'm not exactly sure what you are looking for. What do you mean by Windows VNC server? It seems like you want to be able to login to your machine via a remote session (vnc). As oppose to just viewing a session. 

Check this tutorial here, and see if this is what you want to do

[http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

I think what the OP means (and what I am looking for help on) is the ability to share a desktop without creating an entirely new one.  I can use x11vnc-forever -display :0, but how do I do it as a service so when I reboot, it will automatically run?  Keep in mind that I have Xubuntu, so I don't have all the Gnome goodies installed to make life easier.

Take care,
Russ

---

### Post by rbannan on 2006-07-14
I'm also in the same predicament, I think.  Not entirely sure what the orriginator of this question intended because he wasn't specific enough with the important stuff.  Basically what I want is for my linux box to act like my windows box when it comes to remote desktop.  I dont care how I do it, but I want it to be compatible with a windows box running tightvnc or realvnc or some easy to install on windows equivalent.  I'd like to be able to just boot my pc into linux remotely, and then get a remote session even though linux box is still sitting at a login screen.  OR, if I have logged in, and my pc is just sitting there in screensaver mode, I'd like to just join that session from my windows box at work and pick up right where I left off.  Is this do-able?

---

### Post by gurgle on 2006-07-14
^^ same boat, i think. 

I want to remote into my Ubuntu box at home from work.  At work I have Win XP. 

I would like to create a whole new session, ie localhost:1 so I can be VNC'd into the box while I am logged in. 

I also would like this because I want to force VNC to connect at 1024x768, rather then my monitors native res. 

Thanks!

---

