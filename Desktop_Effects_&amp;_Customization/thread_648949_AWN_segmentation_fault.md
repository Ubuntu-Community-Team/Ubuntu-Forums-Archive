---
title: "AWN segmentation fault"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by shareMenaPeace on 2007-12-24
Hi, 
i tried this  HOW-TO: Awn curves 
I thought this is teh main AWN application / the tutorial says absolutely nothing that there are other stuff required, reallz confusing me...
[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

Than i run in several errors, of missing files which i was able to fix via synaptic package manager except for 

Gnome-Desktop-2.0  it asked.

Than i went on and found on page 129 of the above howto ... another link i realised this is not teh base howto to install awn
so i followed this here

HOWTO: functional eye-candy with Avant-Window-Navigator and Affinity
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)


Now i somehow installed everything, but when i try to start AWN it gives me following error:
```
Screen is composited.
Segmentation fault (core dumped)
 
```
The Manager works just fine ...

SO than i searched and searched and foudn a wiki, project page, blog and lots of stuff but nothing to just install this thing ...than i found this
> It appears that you have two installations of Awn on your computer - one that I assume you compiled yourself that's installed in /usr/local, and the one from reacocard's repository that's installed in /usr. Please remove the one in /usr/local by doing the following:

* open a terminal and change the directory to the directory where you compiled Awn from source.
* run `sudo make uninstall`.
* check to see if awn-manager is still in /usr/local/bin by running `ls /usr/local/bin/awn-manager`. If it's still there, run `sudo rm /usr/local/bin/awn-manager` to get rid of it. (Awn before version 0.2.1 didn't uninstall awn-manager properly)
[https://answers.launchpad.net/awn/+question/16840](https://answers.launchpad.net/awn/+question/16840)
Should i rm the usr folder now, because ther e is no where a uninstall file?

Also after thsi how is the best and easyest way to install this? I prefer synaptic install ...

Thanks for any help

---

### Post by shareMenaPeace on 2007-12-24
Oh and btw im totaly confused by this installs now ....and im close to upgrade somehow to hardy as i see a package there for awn ...

---

### Post by shareMenaPeace on 2007-12-24
Now i cannot boot anymore, not sure if this is related ....

[http://ubuntuforums.org/showthread.php?t=648971](http://ubuntuforums.org/showthread.php?t=648971)
[http://ubuntuforums.org/showthread.php?t=648978](http://ubuntuforums.org/showthread.php?t=648978)

So i guess i need to stick with vista for noe :(

---

### Post by shareMenaPeace on 2007-12-24
ok suddently ubuntu boots again ... i think i had the power cable not connected correct... but no message about this ... starnge problem ...lucky

:popcorn:

---

### Post by shareMenaPeace on 2007-12-24
i deleted the usr folder and rebooted now  awn works :)

---

