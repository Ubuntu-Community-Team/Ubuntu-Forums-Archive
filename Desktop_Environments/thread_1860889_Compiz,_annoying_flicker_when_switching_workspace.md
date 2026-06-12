---
title: "Compiz, annoying flicker when switching workspace"
date: 2011-10-15
forum: Desktop Environments
---

### Post by AnotherLurker on 2011-10-15
Hi all,

Im running a fresh install of Xubuntu 11.10.

I have compiz installed and also im using emerald as the window decorator. 

Card is a GTX570, on an I5 so it certainly isnt a hardware issue. I have the proprietary binary nvidia-current drivers from apt.

When ever i switch workspace with ctrl alt left or right there is a flicker moving to the new workspace, before it is re-drawn. That flicker is whatever was open on the previous workspace, and is very noticable. 

Ok, its a minor gripe but annoying! 

Ive done some googling and found this, but im not sure if its arch specific:

Adding 

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
``` 

to /etc/modprobe.d/nvidia.conf 

Ive noticed there is an /etc/modprobe.d/nvidia-graphics-drivers.conf with some blacklisted modules in, would it work to add the above to that? 

Any help would be greatly appreciated.

---

### Post by AnotherLurker on 2011-10-15
Ok,

Ive narrowed it down to the cube desktop, enabling this gives the flicker. Disabling it and just using workspace switcher and all is well.

Ive have tried adding ppa:ubuntu-x-swat/x-updates and doing an apt update and upgrade to get onto 285.05 drivers but no luck.

It would be nice to get the cube back, if anyone has any suggestions?

Thanks again.

---

### Post by quantum8 on 2011-10-16
I'm hoping there's a simple workaround for this too

---

### Post by stinkeye on 2011-10-16
Happens here, as well as the rotate with window not working(ctrl+alt+shift+Right).
Window moves but then disappears back to previous workspace.

---

### Post by mc4man on 2011-10-17
Just before this started happening with rotate/cube there was an issue with flashing in the workspace switcher - same effect.
Have a bug on that here - with the compiz in 11.10 proposed it appears to be fixed, at least if using wall
(if you switch from rotate/cube to wall one may get flashing still, if so that can be fixed, ask

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/861088](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/861088)

The issues with rotate/cube were mentioned in that bug, but have decided to open a new one specific to cube here - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

It could use confirming & comments about which video card affected users have (and if on open source drivers or proprietary

---

### Post by LewisTM on 2011-10-18
+1

I confirm on Xubuntu Oneiric 64 bit with the latest nVidia drivers
Rotating the cube makes the screen flicker, looks like a split second image of the previous desktop.
Only happens on the active monitor

---

### Post by eternal404 on 2011-12-23
I'm having the exact same problem (posted a video[ here]("http://www.youtube.com/watch?v=vKWLavhaOuw")). I'm also looking for a workaround.

---

### Post by c5wagner on 2011-12-23
I'm having the same problem. For some reason there is no good drivers to support nVidia cards. The other problem is that my fan won't stop on the graphics card...

---

### Post by xXDynamosXx on 2012-01-09
I don't think it's related to Nvidia drivers as I'm using Intel HD2000 graphics on my Pentium G620 and the Issue is still there.

---

### Post by elimitrani on 2012-01-11
I Have a dell 6420 with NVS4200, after setting up the cube i have two problems:

1. the cube is 2d - meaning my desktop flips like a flat surface and switches between only 2 desktops.
2. when the fliping action is completed i get a flicker like you described.

is this indeed a driver issue related to activating the cube on nvidia?

---

### Post by polki@mac.com on 2012-01-12
Open ccsm, go to General, "Desktop Size" tab and make sure you have a virtual horisontal size of 4. The other two can stay at 1 each.
That's what I've done, and it works. Hooray!

EDIT: Sorry, this was for the twopanel problem that elimitrani had.

---

### Post by gabriele.puppis on 2012-01-13
I don't think this fixes the bug, at least in my case.

---

### Post by sodnpoo on 2012-02-18
I fixed it by downgrading to 0.9.4 from natty - instructions are available here: [http://sodnpoo.com/posts.xml/oneiric_compiz_downgrade.xml](http://sodnpoo.com/posts.xml/oneiric_compiz_downgrade.xml)

---

### Post by polki@mac.com on 2012-02-18
Thanks, good to know. The problem is I'm refusing to downgrade. I'm a bitch that way :-D

---

### Post by pixelkalle on 2012-02-24
Same here. Intel HD graphics. Still no fix?

Flicker when switching Workspace via Cubes.

---

### Post by Version Dependency on 2012-02-24
> **pixelkalle said:**
> Still no fix?

Despite the cries for fixing this [bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198"), it is still unassigned.  Apparently, the folks working on Compiz for Canonical aren't interested (or able) to work on it...after all, Unity doesn't even use the cube.  And judging by the activity on Compiz's website, there is a serious lack of developers for the project.  And their forum looks like it nothing more than a haven for spammers now.

Recently distros such as Fedora, OpenSUSE, and Gentoo dropped Compiz.  Might be time to just put Compiz out of its misery.  If it's not dead, it's on life support.

---

### Post by llanitedave on 2012-02-25
I'm using the cube in Unity, and I have a similar issue, although it's not the previous desktop that flickers but the incoming one.  It appears that for about 1/4 of a second the desktop is slightly undersized when it rotates into place.  It pauses for about that amount of time and then it jumps to the full screen.

I notice it, but it's not a big enough deal for me to get worked up over.  It kind of enhances the drama of switching.

---

### Post by cbanakis on 2012-09-05
Found a solution that works for me.

Installing proposed updates, then locking the versions to make the fix permanent.

sudo apt-get install synaptic

sudo apt-add-repository ppa:vanvugt/compiz-preproposed

sudo apt-get update

sudo apt-get install compiz=1:0.9.7.8-0ubuntu1vvpreproposed2   compiz-core=1:0.9.7.8-0ubuntu1vvpreproposed2   compiz-gnome=1:0.9.7.8-0ubuntu1vvpreproposed2   compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2   compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2   compiz-plugins-default=1:0.9.7.8-0ubuntu1vvpreproposed2   libdecoration0=1:0.9.7.8-0ubuntu1vvpreproposed2

(it will downgrade packages, allow it to continue)

Start synaptic

in "Search filter": put "compiz"

select every package that has a (!) next to it.

Select Package -> lock version

(they become red)

exit synaptic

Reboot or Restart X/Compiz.

---

### Post by rjklindsay on 2012-09-27
That fixes it for me too.
Thank you cbanakis!

---

### Post by anthold on 2012-10-26
Thanks [cbanakis]("http://ubuntuforums.org/member.php?u=824651") !

Problem solved

---

### Post by andyofmelbourne on 2013-02-13
Thanks cbanakis! Flicker Eliminated.

---

