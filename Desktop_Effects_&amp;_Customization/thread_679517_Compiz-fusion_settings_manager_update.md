---
title: "Compiz-fusion settings manager update"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by Charlie11x on 2008-01-27
Ok about 10 minutes ago I ran an update which updated the compiz-fusion settings manager.  Well, it flat out stinks and the desktop effects just stopped working.  I was wondering if there was any way to revert to the last version.

---

### Post by biyouboogie on 2008-01-27
replace your /etc/X11/xorg.conf file with the one saved before you made your changes.   Should be /etc/X11/xorg.conf.x  with x being a number.   Most likely the lowest number.   I always save a copy of my "good" xorg.conf to xorg.conf.good so I can replace it when it gets screwed up by updates or changes.    You'll need to have read-write privs on the file if you intend to copy (cp) or move (mv) the good file to a safe haven.

If you're not familiar with Unix commands try these

Open a terminal window.

$ su -
password:    (enter your root password)

$ cd /etc/X11
$ chmod 666 xorg.conf

Now it's read-write for system, owner, and group

$ cp xorg.conf.1 xorg.conf   (assuming xorg.conf.1 is the good file)

You may have to reboot, or just Ctrl+Alt+Backspace to restart your XWindow session manager.


Belive me, dicking around with Visual Effects settings has been a nightmare, and I've had to revert MANY times to a good copy of xorg.conf


Good luck, and Happy ubuntu.... ing.

Earl

---

### Post by Charlie11x on 2008-01-27
When I used your command, cp xorg.conf.1 xorg.conf, i got No such file or directory.
Any ideas?

---

### Post by olavjunior on 2008-01-27
Try 
$ cd /etc/X11
$ dir

Then you see the filename of your xorg.conf-backup file. Then do the cp command with this file. I do believe it's sufficient to press ctrl alt F7 to get back into x, instead of a full reboot

---

### Post by Abu_Dayya on 2008-01-27
> **biyouboogie said:**
> 
$ cd /etc/X11
$ chmod 666 xorg.conf

Now it's read-write for system, owner, and group

Earl

Isn't 666 read-write for _U_ser, _G_roup, _O_thers

---

### Post by blunt on 2008-01-27
I'm having the same problem, almost the same at least, and the backup doesn't help at all, is there any way to revert this now? I can't configure my desktop effects

---

### Post by Charlie11x on 2008-01-27
> **olavjunior said:**
> Try 
$ cd /etc/X11
$ dir

Then you see the filename of your xorg.conf-backup file. Then do the cp command with this file. I do believe it's sufficient to press ctrl alt F7 to get back into x, instead of a full reboot

When I type that command in this is what i get.
```
app-defaults             rgb.txt  xorg.conf   Xsession.d
cursors                  X        Xresources  Xsession.options
default-display-manager  xinit    xserver     XvMCConfig
fonts                    xkb      Xsession    Xwrapper.config

```
Im not exactly sure what to do from here, so if you could help me out that would be great.

---

### Post by Charlie11x on 2008-01-27
Pls I need help.  This is really pissing me off.  Once i finally get everything up and running, there has to be an update to screw everything up.  Why fix whats not broken?

---

### Post by Mramius on 2008-01-27
> **Charlie11x said:**
> Pls I need help.  This is really pissing me off.  Once i finally get everything up and running, there has to be an update to screw everything up.  Why fix whats not broken?

Only you can answer that question as you're the one that ran the update.

---

### Post by blunt on 2008-01-27
I agree that he (and me too) should look more closely at the updates, but, and I don't want to be rude here or ungrateful for ubuntu, but i need an easy system, like most users want.

I tried ubuntu in 2005 when it was just beggining and I quit using it because it wasn't easy at all, had to do a lot of "hacking" to make simple things happen.

Now ubuntu is really great, drivers for everything, awesome desktop effects, but I feel that it's a little disorganized, and I understand Charlie11x, it happened the exact same thing to me, everything was up and running, and when I see an update I think that it is to improve something, not to ruin it. So i admit, i don't know what the update was for, but I'm that type of user that usually don't care, i see update, i click yes, i install it, simple and painless.

I want to maintain ubuntu now, i'm really tired of windoze, but it looks like i'll need a fresh install just because of that compiz update, because i already uninstalled it, installed again and I can't configure it. 

and it kind of sickens me to have 2 or 3 apps that do the exact same thing, like I don't really know anymore where to set how many workspaces I want, there has to be some organization on that level.

---

### Post by xfearxnxloathing on 2008-01-27
just open the synamptic package manager and check the boxes for compiz fusion to remove then logout/in and then search for them in the package manager again and re-install.  should work fine again.

---

### Post by biyouboogie on 2008-01-27
Ok if you want a "good" xorg.conf file where you can be at a decent starting point, type the following command and then reboot your system.    Basically the command can be found in the very top comments of the xorg.conf file and it explains what will happen.

# sudo dpkg-reconfigure -phigh xserver-xorg


I agree with you about the "hacking" required.   I am almost ready to wipe my system and reload from scratch.   Hopefully the new installation will recognize my new GeForce FX 5200 and I will not have all of these problems.  If that doesn't work, then at least I know how to get a better resolution.

THIS is the reason that Microsoft Windows became ubiquitous.   You don't have to dick around to make things work.   Unfortunately for us, the $$ is not there for that kind of development and testing, and the hardware manufacturers have not come on board fully for every flavor of Unix to be supported.   I'm willing to willing to work with ubuntu until it's working like I want it to, but I do get frustrated.

------------

Now, I think it's time you took a primer course in Unix.      Simple commands like   ls -als  instead of dir are helpful.

There's always the man pages if you don't understand the command syntax.   
Just type   man la    
                 man cp
                 man dir
                 man mv
                               and you will learn how these command work.

It's also helpful to know the vi editor when you're in command line mode (no Xwindows running).

If you're going to ubuntu you need to be Unix literate.  It's almost a "must know".

---

### Post by olavjunior on 2008-01-28
> **Charlie11x said:**
> When I type that command in this is what i get.
```
app-defaults             rgb.txt  xorg.conf   Xsession.d
cursors                  X        Xresources  Xsession.options
default-display-manager  xinit    xserver     XvMCConfig
fonts                    xkb      Xsession    Xwrapper.config

```
Im not exactly sure what to do from here, so if you could help me out that would be great.

Well, not sure if your xorg.conf has been changed, since there's no backups of it.. The issue might be something else. Have you tried to change your session at login to failsafe? Then you can try to fix what's broken. 

What graphics card do you have? Nvidia?

---

