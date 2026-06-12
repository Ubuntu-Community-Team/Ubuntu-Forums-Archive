---
title: "switching from Gnome to KDE desktop in Hardy Heron"
date: 2008-05-24
forum: Desktop Environments
---

### Post by alfreddo on 2008-05-24
Hi,

I've been using Ubuntu v.6.06 Dapper Drake with the Kubuntu desktop. Yesterday I upgraded to the latest version 8.04 Hardy Heron, and decided to look at the new Gnome desktop.

Now I am unable to switch back to Kubuntu. The computer boots straight into the Gnome desktop. (the old method was: close programs; press ctrl-alt-backspace to restart X and get login screen; open menu and change to KDE or Gnome).  Now I press ctrl-alt-backspace but do not get a menu.

Any suggestions?

---

### Post by alfreddo on 2008-05-24
Looking at the Gnome helpfiles in Hardy Heron, I see it says:
Press System - Quit
Then press Log Out to to log out of Ubuntu.
At the log-in screen which appears, press Options - Select session.
Choose KDE, press Change Session.

But it doesn't work. After I press Log Out the screen goes black and stays black. No log-in screen appears. 

I then have to reboot the computer, which loads Kubuntu as usual then displays the Gnome desktop again.

Is it possible to switch between Gnome and KDE using a command in the terminal?

---

### Post by ShanghaiTeej on 2008-05-25
If you are stuck in Gnome.  Check out System ->Administration ->  Login Window

You may have bypassed the login window.

---

### Post by alfreddo on 2008-05-25
Hi ShanghaiTeej,

Thanks for responding.

just tried your suggestion, got this message:

GDM (GNOME display manager) is not running.
You might be using a different display manager,
such as KDM (KDE display manager)...
If you wish to use this feature, then your
system will need to be configured to use
GDM instead.

Of course, as well as being unable to switch from Gnome to KDE, when I press Log Off and get a blank screen it means I can't power down properly and can only stop the computer by manually pressing the power switch. Can't be good for the system.

I was able to power down OK from KDE, and switch to Gnome.

---

### Post by ShanghaiTeej on 2008-05-25
Maybe you should open synaptic up and try to install or reinstall "GDM".  Honestly, I have never even thought your problem to be possible.  When I've installed Gnome or KDE on top of Ubuntu/Kubuntu, I've been asked whether I want GDM or KDM as my login manager.  You have a very weird problem my friend.

---

### Post by lswest on 2008-05-25
> **ShanghaiTeej said:**
> Maybe you should open synaptic up and try to install or reinstall "GDM".  Honestly, I have never even thought your problem to be possible.  When I've installed Gnome or KDE on top of Ubuntu/Kubuntu, I've been asked whether I want GDM or KDM as my login manager.  You have a very weird problem my friend.

He's running Kubuntu, so it's running the KDM.  You will need to edit it using the KDE version of the login window (which should be accessible in GNOME too).  do **NOT** just install gdm, it will conflict with your KDM and probably run into quite a few problems.

try ```
sudo kcontrol
``` in the terminal and then find your login window preferences, and make sure it is running.

---

### Post by ShanghaiTeej on 2008-05-25
Thanks for correcting my horrible advice!

---

### Post by lswest on 2008-05-25
> **ShanghaiTeej said:**
> Thanks for correcting my horrible advice!

It wasn't horrible advice, it would have been good advice - if he were using the GDM (he didn't specify which he was using, but i assume it is the KDM, which would explain it).  If my post makes it seem like horrible advice, it's more so the OP reads it before doing anything ;)

---

### Post by ShanghaiTeej on 2008-05-25
> **lswest said:**
> It wasn't horrible advice, it would have been good advice - if he were using the GDM (he didn't specify which he was using, but i assume it is the KDM, which would explain it).  If my post makes it seem like horrible advice, it's more so the OP reads it before doing anything ;)

Oh, I completely understand.  It's all about actually helping people, which is why it's good that people like you care enough to give the correct advice.  Which is why this community is pretty awesome!  Take it easy.

---

### Post by Xiong Chiamiov on 2008-05-26
You might have a corrupted version of the login manager (or be trying to load one that doesn't exist), so if you do a
```

sudo dpkg-reconfigure gdm

```
(or kdm, or kdm-kde4) then you'll be able to choose which login manager you want.

---

