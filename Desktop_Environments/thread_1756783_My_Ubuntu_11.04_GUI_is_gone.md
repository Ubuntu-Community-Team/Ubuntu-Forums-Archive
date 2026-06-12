---
title: "My Ubuntu 11.04 GUI is gone"
date: 2011-05-12
forum: Desktop Environments
---

### Post by Austinl on 2011-05-12
Well I wanted my Unity side bar to be always up and stop hiding when i open a windows, i looked it up on the internet and installed several pieces of software.  Including Confiz(i think) and it said it needed a package, so i did apt-get and installed it.

After it installed my Interface went all strange, so i reset, and when i relogged in my interface was gone!

I can only see my desktop and access Chrome, i cant do Alt+F2 either! I am really confused in what to do and i cannot do much other use the desktop, and press Ctl+Alt+Del. So im stumped!

Any help would be great.
Austinl

---

### Post by treasonvoice on 2011-05-12
Try running in failsafeX or choosing a different desktop environment on startup and uninstall those packages. If you don't remember what they are called, you will find a log in /var/log/apt/history.log. That way you can open your synaptic and uninstall.

That help?

---

### Post by treasonvoice on 2011-05-12
Also, surely setting sidebar behaviour is easy using the unity plugin in ccsm? If you need some help, let me know. Unity has a few teething issues it needs to have sorted out if Canonical (read Mark Shuttleworth) plans to scrap classic in 11.10.

---

### Post by Austinl on 2011-05-12
Hm, well i did try and open it in a different desktop and it just looked the same...Is there a way i could run a file from the desktop to run a script to get the interface back?

---

### Post by abohsin on 2011-05-12
When you install Compiz, other packages are also included, which the new version of Ubuntu seems to detect, and thus logs you into the original Gnome desktop. Since Unity is new, just stick to the existing graphics provided, until proven otherwise :)

---

### Post by treasonvoice on 2011-05-12
If there is I'm not nearly technical enough for that. Have you tried using recovery/safe mode?

---

### Post by treasonvoice on 2011-05-12
Also, what graphics card you using?

---

### Post by Austinl on 2011-05-12
Intel Mobile Chipset 4, And i logged out and then back in in safe mode and again it looked the same, so do i have to restart, login in safe mode?

---

### Post by 23dornot23d on 2011-05-12
> 
Well I wanted my Unity side bar to be always up and stop hiding when i  open a windows, i looked it up on the internet and installed several  pieces of software.  Including Confiz(i think) and it said it needed a  package, so i did apt-get and installed it.

After it installed my Interface went all strange, so i reset, and when i relogged in my interface was gone!






Might be worth checking you have not somehow removed the compiz files needed to run
Unity ,,,,

do a screenshot from Synaptic package manager after searching for compiz as below

[IMG]http://img835.imageshack.us/img835/2836/compizi.jpg[/IMG]

I may have a few extra here to you ... but do a screenshot .... please .... and post .... if you can.

---

### Post by treasonvoice on 2011-05-12
Yip. See what happens. I'm no tech... but it seems like you might just have to - should push come to shove - do a reinstall. But I can't see failsafeX not working. I'm afraid if that doesn't work then there is nothing I can do for you, and someone infinitely wiser and nerdier would have to step in and be a hero. Good luck. Sorry.

---

### Post by treasonvoice on 2011-05-12
> **23dornot23d said:**
> Might be worth checking you have not somehow removed the compiz files needed to run
Unity ,,,,

do a screenshot from Synaptic package manager after searching for compiz as below



Problem is, as I see it, he can't even GET to synaptic because his GUI is non-responsive.

---

### Post by Austinl on 2011-05-12
The funny thing is, if i make a empty file on the desktop, and open it in notepad, it will open it. And chrome works too.

---

### Post by treasonvoice on 2011-05-12
can you create a launcher?

---

### Post by 23dornot23d on 2011-05-12
Does Alt+F2 work ..... 
( I have a feeling they changed this to workspace switcher now though )

we need to open a terminal or someway to input the commands ....
as your GUI is working if you can run chrome ..... my guess is its the compiz settings that are messed up

compiz --replace
or 
unity --reset 

may clear the problem ..... if you can enter these commands ...

> 
can you create a launcher?


Good thinking ..... another way of starting something up .......

---

### Post by treasonvoice on 2011-05-12
> **23dornot23d said:**
> Does Alt+F2 work ..... 
( I have a feeling they changed this to workspace switcher now though )

we need to open a terminal or someway to input the commands ....
as your GUI is working if you can run chromium ..... my guess is its the compiz settings that are messed up

compiz --replace
or 
unity --reset 

may clear the problem ..... if you can enter these commands .....

i'm thinking he could create a launcher on his desktop... what must the command be though to get to synaptic?

---

### Post by treasonvoice on 2011-05-12
or perhaps to ccsm?

---

### Post by wilee-nilee on 2011-05-12
> **abohsin said:**
> When you install Compiz, other packages are also included, which the new version of Ubuntu seems to detect, and thus logs you into the original Gnome desktop. Since Unity is new, just stick to the existing graphics provided, until proven otherwise :)

Not true compiz is already installed enabling the config manager changes nothing.

Op reset compiz to default after removing the package that caused problem, and run.
unity --reset

---

### Post by 23dornot23d on 2011-05-12
Think you would have to run it as sudo ..... 

gksudo synaptic

I think I would try this first though if he can ..... 

unity --reset

---

### Post by treasonvoice on 2011-05-12
Ok. Hopefully AustinL can sort this out. I'm off to sleep coz I've been awake for more than 24 hours, but I'll check up on this thread in the morning and see if I can help at all.

Good luck Austin. Try creating a launcher on your desktop to get into synaptic and reinstall compiz or whatever it takes.

---

### Post by Austinl on 2011-05-12
Right i'm in failsafeX now, here is the history file:

```

Start-Date: 2011-05-12  21:17:23
Remove: ubuntu-desktop:amd64 (1.220), unity:amd64 (3.8.12-0ubuntu1), libcompizconfig0:amd64 (0.9.4-0ubuntu2), compizconfig-backend-gconf:amd64 (0.9.2.4-0ubuntu1), compiz-plugins-main:amd64 (0.9.4+bzr20110406-0ubuntu2), compiz-gnome:amd64 (0.9.4+bzr20110415-0ubuntu2), compiz-plugins:amd64 (0.9.4+bzr20110415-0ubuntu2), compiz:amd64 (0.9.4+bzr20110415-0ubuntu2), compiz-fusion-plugins-main:amd64 (0.9.4+bzr20110406-0ubuntu2), compiz-core:amd64 (0.9.4+bzr20110415-0ubuntu2)
End-Date: 2011-05-12  21:17:33

Start-Date: 2011-05-12  21:17:42
Install: compiz-plugins:amd64 (0.9.4+bzr20110415-0ubuntu2, automatic), compiz-core:amd64 (0.9.4+bzr20110415-0ubuntu2)
End-Date: 2011-05-12  21:17:45

Start-Date: 2011-05-12  21:20:24
Remove: compiz-plugins:amd64 (0.9.4+bzr20110415-0ubuntu2), libboost-serialization1.42.0:amd64 (1.42.0-4ubuntu2), compiz-core:amd64 (0.9.4+bzr20110415-0ubuntu2)
End-Date: 2011-05-12  21:20:26

Start-Date: 2011-05-12  21:20:42
Install: compiz-plugins:amd64 (0.9.4+bzr20110415-0ubuntu2, automatic), libboost-serialization1.42.0:amd64 (1.42.0-4ubuntu2, automatic), compiz-core:amd64 (0.9.4+bzr20110415-0ubuntu2)
End-Date: 2011-05-12  21:20:45

Start-Date: 2011-05-12  21:21:00
Install: libcompizconfig0:amd64 (0.9.4-0ubuntu2, automatic), python-compizconfig:amd64 (0.9.4-0ubuntu1, automatic), compizconfig-settings-manager:amd64 (0.9.4-0ubuntu2)
End-Date: 2011-05-12  21:21:06
```

Yay! I done it people.  Basically i rebooted to failsafeX and then I went into Compiz utility manager or what not, and enabled Ubuntu Unity, this fixed it right up for some reason.

Thanks for changing my diaper guys :) I'm still quite new to this Linux-majig, but you give me faith to not give up :P

---

### Post by treasonvoice on 2011-05-13
Awesome. Glad you got it sorted. That's the thing about Ubuntu that i've noticed so far in my year of usage - you can break it as much as you want but there always seems to be some way to fix it. Very robust.

Ubuntu: You never know what not to mess with until you're presented with a command line.

Enjoy Austin

Also pretty chuffed that my first instinct was more or less correct. Nice.

---

