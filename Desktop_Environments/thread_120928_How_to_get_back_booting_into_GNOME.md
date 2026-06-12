---
title: "How to get back booting into GNOME?"
date: 2006-01-23
forum: Desktop Environments
---

### Post by rskovacs on 2006-01-23
Hello again everyone,

The problem I am having is that my system boots into the terminal rather than into the usual (for me) GDM/GNOME, and I don't know exactly what caused this change.  I mean, all I have to do is login at the terminal screen, and then type ```
sudo gdm
``` But I used to not have to do this, of course.  How did things probably end up this way?  Here goes:

Recently I was having problems with upower, so I uninstalled it according to the advice I got [here]("http://www.ubuntuforums.org/showthread.php?t=115637"), and reinstalled usplash.  This is probably not the problem; what I assume is the issue is that for some reason I had the idea that it would be a good idea to then type this 
```
sudo dpkg-reconfigure linux-image-`uname -r`
``` into the terminal before rebooting, since that does...well, actually, I don't exactly know, so I *probably* ;) shouldn't have done it.   But it seemed like a good idea at the time :(

So now when I start up my computer, the boot-up process has all the right graphics (so I have that going for me) but it ends by bringing up the terminal and not the GDM.  What did I do, and how can I fix it?

---

### Post by GreyFox503 on 2006-01-23
I'm not at my Ubuntu box right now, but try to add gdm to the default runlevel by issuing this command: (either with sudo or as root)

```
rc-update add gdm default
``` 
It should output a message either confirming success, telling you it was already there, or some other message.  To see if it worked, just restart your computer, and gdm should load.

If it doesn't work/you don't like and you want to undo it, issue:

```
rc-update del gdm default
```

---

### Post by rskovacs on 2006-01-24
When I try to follow your suggestion, I get a "command not found" error.  I thought maybe I had to install rc-update, but it's not in the repositories.  Maybe it was a typo?  Still, thanks for your reply.

---

### Post by GreyFox503 on 2006-01-25
Ugh.  I've been spending a *little* too much time setting up Gentoo.  Sorry, you're right, that command won't work for you.  Try this one.  It will try to add gdm to runlevel 2, starting at 13.  Everything is important, including the spaces and the period.  It probably needs to be run as root/sudo.

```
update-rc.d gdm start 13 2 .
``` 

I checked my Ubuntu system out.  My default runlevel is 2 and gdm was set to start at 13.  Let me know if this works.

---

### Post by rosslaird on 2006-01-25
You can also do this by way of the following two steps:

sudo dpkg-reconfigure gdm (choose gdm from the list)
sudo rcconf (choose gdm)

Then reboot.
You may have to install rcconf from the repositories.

Cheers.

Ross

---

### Post by rskovacs on 2006-01-28
Thanks for your help guys.

I tried both actually. When i tried update-rc.d it says System startup links for /etc/init.d/gdm already exist.  Similarly, when i ran rcconf, gdm was already selected.  So supposedly GDM is set to run on boot, but it really doesn't.  Huh??

---

### Post by GreyFox503 on 2006-01-28
[quote=rskovacs]So supposedly GDM is set to run on boot, but it really doesn't.  Huh??[/quote] 
Yeah, that's what it sounds like.  Maybe a little more info would help.

Run this command:

```
grep "initdefault" /etc/inittab
``` 
It will output a line that looks like this:

```
id:2:initdefault:
``` 
Whatever number is on that line (probably a 2) is your default runlevel.  I don't of any reason why it should be different, but it can't hurt to check.

Then, post here the output of this command:

```
ls /etc/rc2.d/
``` 
Modify this command if necessary so that the number is the same one you found earlier (the default runlevel).

---

### Post by rosslaird on 2006-01-28
> I tried both actually. When i tried update-rc.d it says System startup links for /etc/init.d/gdm already exist. Similarly, when i ran rcconf, gdm was already selected. So supposedly GDM is set to run on boot, but it really doesn't. Huh??

With regard to my technique, I forgot to mention that in rcconf you have to makes sure that all other login managers (xdm or kdm, or perhaps entrance) are de-selected.

But other than that, I don't know. You seem to have tried quite a few things, and it's weird that this is persisting.

Ross

---

### Post by rskovacs on 2006-01-29
OK, to respond to both suggestions:

It seems 2 is the default runlevel, and the contents of /etc/rc2.d/ are:
```
K19hplip        S10sysklogd  S20apmd          S20rsync    S98usplash
K74bluez-utils  S11klogd     S20hotkey-setup  S25mdadm    S99acpi-support
K86ppp          S12dbus      S20makedev       S89anacron  S99fetchmail
S05vbesave      **S13gdm**       S20pcmcia        S89atd      S99rmnologin
S10acpid        S19cupsys    S20powernowd     S89cron     S99stop-bootlogd
```
Also, there are no other login managers running according to rcconf.
 
Once again, thanks for your help.

---

### Post by GreyFox503 on 2006-01-30
Well, it's definitely where it should be.  And it's set to start, not stop, and none of the other entries are for stopping it either.  You could check to make sure it's executable, but I don't know why it wouldn't be.

Well,  the pragmatic solution would just be to get it working any way you can.  If you know a certain command works to start it (like "sudo gdm") then you could create your own startup script by modifying one of the ones already in there that executes this command.  Anything you put there shouldn't need 'sudo' in front of it.  So in this case it would just be "gdm".

---

### Post by Jasman on 2006-03-08
I just dealt with this same problem on a daily build of Dapper. Have you checked to see whether the files /etc/init.d/gdm and its linked file, /etc/rc2.d/S13gdm, have anything in them? If not, you need the contents of /etc/init.d/gdm from someone to paste in (as root or with sudo). For some reason, mine was blank, and that was in addition to the fact that gdm and ubuntu-desktop didn't install initially.

---

