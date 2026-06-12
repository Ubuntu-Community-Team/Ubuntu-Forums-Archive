---
title: "Log into gnome classic is ok, cannot log into regular gnome"
date: 2016-05-17
forum: Desktop Environments
---

### Post by Bartje on 2016-05-17
Hi all,

after upgrade to 16.04 I cannot log into regular gnome. I keep being sent back to the login screen. Using Gnome Classic however lets me log in, using it now.
Is there a way to fix this?

What I have done so far:

-sudo dpkg-reconfigure lightdm
-sudo dpkg-reconfigure gdm
-renamed .Xauthority
Udate: 
-installed all possible nvidia drivers, from nouveau to proprietary, to no avail.
-sudo apt-get install --reinstall gnome-shell did not change anything

I have installed the wayland gnome, sends me back to the login screen too. Fallbacksession works fine.

all tips to fix this are welcome :-)

I edit this post because it is finally solved. As in one of the replies I managed to get in to regular gnome by entering the next thing into the terminal:
```

gnome-shell --mode=user -r &

```
Which left me to wonder why that works, and not by selecting gnome in gdm or lightdm. So there was only one thing left: something in the entry of gdm must have been wrong.
So I searched for how to change the entries that are listed in gdm. I found out that these login managers read "/usr/share/xsessions and list them when you try to select which DE you want to use.

In that directory I found:

GNOME
Gnome Klassiek
Gnome Flashback (Compiz)
etc... 

so I looked into the GNOME file, which is only a shortcut to launch a command. The command it had to run was:

```
gnome-session --session=gnome
```

I compared it with the shortcut called Gnome Klassiek That contained the command:
```
gnome-session-classic
```

So I made a duplicate of the GNOME shortcut (as backup) and edited the command of the original to:
```
gnome-session
```

Then a reboot et voila: fixed :-) :-D :-p

I hope this info helps others.

grtz,
Bart

---

### Post by kansasnoob on 2016-05-18
I have a similar issue, but mine won't even boot into a flashback session, on this hardware:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Nothing but a login bounce, even with the nomodeset parameter set :(

Sadly i have no answer but I'll give you a free bump.

---

### Post by Bartje on 2016-05-19
@ kansasnoob  Thanks for the bump :-)
I guess you have tried everything I have already. I just did an update, gnome shell was part of the updates, but no change.

What I find strange in my case is that Gnome Classic actually works. 
I mean it is not that different from Gnome-shell, it even is Gnome Shell with a top bar a bit differently organised and (sadly badly) colored and with an aditional bottom bar.
It can't be a big issue, it must be one small detail that has to be changed to get it working, but which?

---

### Post by Bartje on 2016-05-19
ok, I made some progress, not solved yet, but progress nevertheless.

I found out that one can switch between gnome classic and gnome shell using the info on this site:
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Desktop_Migration_and_Administration_Guide/what-is-gnome-classic.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Desktop_Migration_and_Administration_Guide/what-is-gnome-classic.html)

And it actually works: gnome shell works when I start from gnome classic and then enter the command: 
```

gnome-shell --mode=user -r &

```

But login in by selecting Gnome does not work yet.

---

