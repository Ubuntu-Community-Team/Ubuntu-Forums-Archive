---
title: "How do I stop X from starting at boot?"
date: 2006-10-16
forum: Desktop Environments
---

### Post by Vashu on 2006-10-16
I'm running an small ubuntu server on an old machine with low resources. I installed xubuntu desktop on it for the times CLI mode was too overwhelming (linux noob) but that have it set up like i want and can do most of the things I want with CLI commands, i would like to make xserver start only when i command it to in order to save the resources for something else. 

How can i do that without unninstalling it?

---

### Post by JonahRowley on 2006-10-16
This probably wouldn't save all that many resources, unless you're particularly starved for them.  If it sits idle, most of XFCE will be swapped out to disk anyway.  Assuming you're using Dapper (or anything before edgy), you can do this easily by **apt-get install sysv-rc-conf**, then **sudo sysv-rc-conf** and remove gdm from runlevel 2.

Edit: this might actually work fine in edgy, but I don't know anything about upstart yet.

---

### Post by Blario on 2007-03-21
For the Edgy solution, the Ubuntu recommended method is to use 'update-rc.d'.  In order to remove the symlinks in the rcX.d directories, you'd use 'sudo update-rc.d -f <name>'.

"man update-rc.d" for more info.

---

### Post by scxtt on 2007-03-21
as long as you don't have a display manager (xdm/kdm/gdm) set to start for the runlevel you boot to (level 2, generally) - you won't get a GUI starting up til you type startx ...

so remove the symbolic links in /etc/rc2.d that point to and display manager ...

---

### Post by Mr. C. on 2007-03-21
> **JonahRowley said:**
> This probably wouldn't save all that many resources, unless you're particularly starved for them.

Hmmm... Have you looked at the *resident* set size (i.e. the working set of pages) of all GUI processes.  I see about 100Meg.  For a small system, that's not insignificant.

MrC

---

### Post by ubix on 2007-03-21
Since **/etc/inittab** philosophy has changed, and they started to use **upstart**, I got confused too, however, they say not much has changed, and that the old ways should still work; see:```
cd /usr/share/doc/upstart && zcat README.Debian.gz |less
```In the above document they say:> How do I change the default runlevel?
-------------------------------------

Edit the /etc/inittab file, if you installed edgy fresh you'll need to
create it.  Locate, or write, the following line:

    id:N:initdefault:

Where N is the default runlevel, change this to match.
However, I found the above does not work.

But to return to your question, of **How do I stop X from starting at boot?**, you can do two things:```
sudo mv /etc/init.d/gdm /etc/init.d/gdm-
```Or alternatively you could uncheck **Graphical login manager (GDM)** in [COLOR="Blue"]**System->Administration->Services**[/COLOR]. I prefer to rename **/etc/init.d/gdm**, because you do not need to run GUI to reverse your action.

---

### Post by Mr. C. on 2007-03-21
Or why not have you cake and eat it to.  Rename the GDM link in rc3.d to a K script, change the default runlevel to 3 as suggested.  The system will boot into console, and when you want to go GDM, just type init 5.  There was utility in the various run levels.

MrC

---

### Post by tomchuk on 2007-03-21
Or why not remove gdm from the default runlevel (2) and just run telinit 3 (or 4 or 5) when you want X to start. Then you save yourself the step of setting up an inittab.

---

### Post by Ruskie on 2007-09-24
All these methods you have posted may work  (I'm sure they do actually) but they're terribly inelegant and unpractical.
Those screw up all the beauty and simplicity of configurable runlevels. Is it a temporary feature of the switch to upstart or shall we consider inittab gone and forever?

Thanks

---

### Post by Ruskie on 2007-10-03
I have found answer to my own question. I hope this clarifies situation for all newcomers and everybody who got confused by the switch to upstart boot system.

Indeed, runlevels still exists, and they continue to be "driven" by /etc/inittab, more specifically by the initdefault line. What has changed are basically 2 things:

1) Default runlevel is now runlevel 2
2) All runlevels defaults to "graphical mode", i.e. they all start either gdm or kdm, depending on which window manager you use

SOLUTION FOR ALL THOSE WHO DO WANT TO START UBUNTU IN "CONSOLE MODE"
It's easy to do once you figured out previous things.
Many people gave the right suggestion: "rename gdm in rc.d" etc. etc., but the easier way for those who (like me) are not really experienced in messing with rc directories...

1) Choose a runlevel you want to use for "console mode": I recommend runlevel 3 because it is the "old" console mode runlevel
2) Set it to be the default runlevel in inittab: modify the initdefault line as such:
id:3:initdefault:
3) Install the package sysv-rc-conf (you can figure out on your own how to install it, can't you?)
4) Run sudo sysv-rc-conf
5) Locate in the column for runlevel 3 the line for your login manager: either gdm or kdm or whatever
6) Uncheck the box for it to start. Now at runlevel 3 gdm won't be started (but you did not have to mess with scripts!)
7) Reboot

You will have now console mode. If you want to start Gnome/Kde/Whatever, simply launch startx.
If you want to return to graphical login, change back initdefault line in inittab so that default runlevel is 2.

Hope it helps

---

### Post by qil on 2007-10-03
where do i edit the inittab ? ive tried pico /etc/inittab, that does not exist here.. :0

cheers,
Avi.

---

### Post by Ruskie on 2007-10-03
If you do not have inittab it's because you installed from scratch a 7.04 version instead of updating from an old one (like I did). In that case, you can create it on your own.
I'm not sure, but since it is now there only to control default runlevel, you don't need all the stuff; the initdefault line should be enough:

id:N:initdefault:

Where N is the default runlevel you want (for example: 2)

---

### Post by medde on 2007-10-11
I've cut & paste this text somwhere I don't remember were but it works and is fairly simple to use.

****
You can prevent automatic running of the GUI when you boot your debian machine by disabling your login manager be it KDM, GDM or XDM from running at boot time. To disable the login manager from automatically running at boot up, run the following command as root

#update-rc.d -f gdm remove

Replace gdm with kdm or xdm if they are what you use.

To start X manually, you would then have to login at the command prompt and enter the command startx.

To reset your login manager so that it runs at boot up, do

#update-rc.d -f gdm defaults

****

Never mind the debian in the text Ubuntu is almost a debian system.

---

### Post by WaterBreath on 2007-10-25
FYI, I tried medde's recommendation on a fresh 7.04 install, and all it got me was a hung boot sequence where it would normally start X.

I will try the other method, editing the runlevels to remove graphical mode.  I searched the web far and wide to find out why "init 3" wasn't getting me to the CLI in Ubuntu, and almost thought I had gone mad before I finally found this thread.

---

### Post by WaterBreath on 2007-10-25
Alas it did not work.  Still got a freeze at "Running local boot scripts".

Any ideas as to what would cause this?  I really want to boot to CLI so that I can try out some nVidia beta drivers.

---

### Post by BobCFC on 2007-12-22
> **WaterBreath said:**
> Alas it did not work.  Still got a freeze at "Running local boot scripts".

Any ideas as to what would cause this?  I really want to boot to CLI so that I can try out some nVidia beta drivers.



You can stop gnome temporarily while you install the drivers.  This is what I do:


in gnome-terminal type:
```

sudo /etc/init.d/gdm stop

```

crtl-alt-F2   to switch to virtual terminal, login and install drivers:

```
sudo sh nvidia.xxx.run

sudo /etc/init.d/gdm start

```

You may need to press crtl-alt-F7 again to switch back to X, or it may do for you i forget.


BTW:  make sure you have removed the ubuntu drivers first: **sudo apt-get remove nvidia***

and you need the compiler installed of course:  **sudo apt-get install build-essential**

---

### Post by matey3 on 2008-02-21
> **medde said:**
> I've cut & paste this text somwhere I don't remember were but it works and is fairly simple to use.

****
You can prevent automatic running of the GUI when you boot your debian machine by disabling your login manager be it KDM, GDM or XDM from running at boot time. To disable the login manager from automatically running at boot up, run the following command as root

#update-rc.d -f gdm remove

Replace gdm with kdm or xdm if they are what you use.

To start X manually, you would then have to login at the command prompt and enter the command startx.

To reset your login manager so that it runs at boot up, do

#update-rc.d -f gdm defaults

****

Never mind the debian in the text Ubuntu is almost a debian system.


You're da Man!
:)
Thank you and Thanks To Everybody!

(Now if I could somehow put those line in my Grub menu...umm that'd be so gr8!)!?

---

