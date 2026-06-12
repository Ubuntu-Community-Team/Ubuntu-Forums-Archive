---
title: "Gnome won't run at startup."
date: 2009-11-16
forum: Desktop Environments
---

### Post by Ordinary12 on 2009-11-16
Hey Guys:

I'm running Ubuntu 9.10 and when I restarted the laptop I noticed a different looking login screen than the default one that was there before.  I picked my name and entered the password and Ubuntu started running the OS as normal but when it finished it didn't bring up Gnome.  All I see is a black screen with a small command line terminal in the top left corner of the screen.  I installed the newest Gnome desktop but when I restart the laptop I keep getting the command line terminal.  Does anyone have any ideas?

---

### Post by themusicalduck on 2009-11-16
First try typing in this command:

```
startx
```

and see what comes up.

Also might be worth trying this:

```
sudo gdm
```

and see what comes up and type any messages here.

---

### Post by Ordinary12 on 2009-11-16
When I type startx I get the following message:

X: user not authorized to run the X server, aborting.


When I type sudo gdm I get the following message:

**(gdm-binary:2819): WARNING **: Failed to aquire org.gnome.DisplayManager

**(gdm-binary:2819): WARNING **: Could not aquire name; bailing out

---

### Post by dueland on 2010-01-22
I'm having the exact same problem, did you ever find a fix for it?

I'm also running ubuntu 9.10 with the latest nvidia driver (195.30)

---

### Post by kimberlite on 2010-01-22
> **Ordinary12 said:**
> When I type startx I get the following message:

X: user not authorized to run the X server, aborting.



Try ```
sudo startx
```

---

### Post by dueland on 2010-01-22
I get a fatal error stating that an x-server is already running (which it is, I'm currently writing this message under the bugged system). If not any server is running, it says, I should remove /tmp/X0.lock.

---

### Post by dueland on 2010-01-23
I removed gnome-panel dependencies (the package itself wasn't installed), and then installed gnome-panel. I restarted and now it works..

---

### Post by ross.ackland on 2010-01-26
> **Ordinary12 said:**
> Hey Guys:

I'm running Ubuntu 9.10 and when I restarted the laptop I noticed a different looking login screen than the default one that was there before.  I picked my name and entered the password and Ubuntu started running the OS as normal but when it finished it didn't bring up Gnome.  All I see is a black screen with a small command line terminal in the top left corner of the screen.  I installed the newest Gnome desktop but when I restart the laptop I keep getting the command line terminal.  Does anyone have any ideas?

I have the same behaviour, after I login I get a black screen with an xterm in the top left corner and no window manager. I can enter startxfce4 and the window manager launches, so there must be something broken in the startup process in my login scripts. I have looked in the log files Xorg.0.log and gdm/:0.log and cant see any errors. 

Im just guessing, but it seems that after gdm login process something is not getting to my ~./config/autostart scripts. 

Im running a standard Karmic/Mythbuntu installation. Any help on where I should be looking would be greatly appreciated.

---

### Post by Ordinary12 on 2010-02-24
They way I fixed everything was by removing everything related to Gnome, restarted my laptop, and re-installed Gnome from the command prompt.  I didn't lose anything so I'm happy with that solution.

sudo apt-get remove gnome
sudo apt-get install gnome

---

### Post by engine on 2010-03-17
The advice from Ordinary12 looked clear and understandable, which is a a plus, but I soon ran in to more problems :-{
```
>sudo apt-get remove gnome
```
:
:
> Package gnome is not installed, so not removed

OK, so let's try and install it!
```
>sudo apt-get install gnome
```
:
:
> Some packages could not be installed
:
gnome: Depends: gnome-desktop-environment (=1:2.22.2~4ubuntu8) but it is not going to be installed
Depends: gnomle-vfs-obexftp but it is not installable
E: broken packages

Might try an apt-get on gnome-desktop-environment, but I'm not holding my breath! and any farther advice will be welcome. At least I'm not the only person who's had this strange problem ...

---

### Post by engine on 2010-03-17
```
>sudo apt-get install gnome-desktop-environment
:
gnome-desktop-environment: Depends: fast-user-switch-applet (>=2.22.0) but is not installable
```

So what I'm trying to install depends on something that's not installable ... I think I'll give up for today :-{

---

