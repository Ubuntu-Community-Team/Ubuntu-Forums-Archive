---
title: "Need assistance installing Debian/Hurd. :)"
date: 2008-03-28
forum: Debian
---

### Post by Omnios on 2008-03-28
Hi I have read about the Hurd a long time ago and want to install it as a tri boot on my older tower server and to play with installs.
 
The Hurd page is here.
[http://www.gnu.org/software/hurd/hurd.html](http://www.gnu.org/software/hurd/hurd.html)
 
A quote of Hurds description from there web site as follows.
 
> 
 
The GNU Hurd is the GNU project's replacement for the Unix kernel. The Hurd is a collection of servers that run on the Mach microkernel to implement file systems, network protocols, file access control, and other features that are implemented by the Unix kernel or similar kernels (such as Linux). Currently, the Hurd runs on IA32 machines. The Hurd should, and probably will, be ported to other hardware architectures or other microkernels in the future. 
 
A quote on Hurds developement staus is as follows.
 
> 
 
The Hurd, together with the GNU Mach microkernel, the GNU C Library and the other GNU and non-GNU programs in the GNU system, provide a rather complete and usable operating system today. It is not ready for production use, as there are still many bugs and missing features. However, it should be a good base for further development and non-critical application usage. 
The GNU system (also called GNU/Hurd) is completely self-contained (you can compile all parts of it using GNU itself). You can run several instances of the Hurd in parallel, and debug even critical servers in one Hurd instance with gdb running on another Hurd instance. You can run the X window system, applications that use it, and advanced server applications like the Apache webserver. 
On the negative side, the support for character devices (like sound cards) and other hardware is mostly missing. Although the POSIX interface is provided, some additional interfaces like POSIX shared memory or semaphores are still under development. All this applies to the current development version, and not to the last release (0.2). We encourage everybody who is interested to try out the latest development version, and send feedback to the Hurd developers. 

 
Also Debian had made a OS veresion using the hurd kernel. Which is available here.
 
[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)
 
The install disk info is as follows. 
 
[http://www.debian.org/ports/hurd/hurd-cd](http://www.debian.org/ports/hurd/hurd-cd)
 
I want to use my Ubuntu isntall to manage Grub and also would like some more info on the mouning partitions part. 
 
I would also like to use my home difectory for my personal files but could use another username for hurd config files.
 
 
any help or advise would be apreacieted.
 
 Edit doing some heavy reading and things are looking up maybe tomoro I will try a install.
 
 Apperently the latest Debian GNU/Hurd install CD does not have the old 2Gig hard drive limit and things are looking up. The old 2gig limit. Reading old posts on this almost turned me off from trying but kept reading and found out about that change. More I read the install looks less scarry. Probably going to try installing it tomoro.
 
 Also hoping to be able to make packages for it so I can break stuff with packages like Gnomad lol with usb and stuff lol.

---

### Post by Omnios on 2008-03-29
Weee loads of fun!!!!!!!
 
Found a Hurd live cd at [http://www.superunprivileged.org/hurd/live-cd/](http://www.superunprivileged.org/hurd/live-cd/)
It does not have xserver or a GUI but brings back warm memories.
 
K Hurd is not ready yet it loaded ok and I could look around and stuff. Find it very intersting so far. Anyways got the Live Cd to see if would run on my computer but am having some fun with it.
 
Also found another interesting hurd install that auto installs grub and sets up xserver but I have a dual boot system and do not want Hurd to install Grub but rather mod the Ubuntu grub entry to see Hurd.
 
[http://magizoom.blogspot.com/2008/02/release-of-lx-installer-for-debian.html](http://magizoom.blogspot.com/2008/02/release-of-lx-installer-for-debian.html)
 
Spent a day reading about hurd and it seems to be getting a bit more advaned than my original reading. I did a google advanced search with a date filter and get more up to date info. The default its where very old. 
 
He he I got a 'micro kernel' :)
 
Free as in unix
(bad joke but could not resist)

---

### Post by Omnios on 2008-04-30
Hi been banging my head off the wall for the last three days. I desided to try install gnu hurd before installing the new Ubuntu but had phun anyways. I found this that is supposed to install the hurd kernel and run install the tarball and set it up as apposed to cross installing the debian hurd package. 
 
[http://www.projecthurd.tk/](http://www.projecthurd.tk/)
 
 Prob is its proke,,,, It will set up the base system but the xserver part is proken as it did not find the xorg package either on the LX1 hurd cd nor did it find it on the debian disks I downloaded. Apperently the first two disks have what you need. 
 
 I have tried a hole bunch of installs so far but always seems to end up with a proken system. Did a lot of hack jobs with using the lx and running install scripts.
 
 Results so far are dissapointing as got up to a dist upgrade but apt-get was gone. and could not seem to mount the cd.
 
 Got up to setting up a root and user accound and even got my seperate /home partition mounted but lost the joy when I started trying to use apt- to upgrade packages and slamed into a brick wall with dep hell. Seemed everything wantd different versions of the same packages or packages missing.
 
 Also the is a libc0.3 fix that did not work on this try. I think the problem so far is different versions and source lists. More work needs to go into this as a web server is suppposed to be possible and may push hurd farther right now than a desktop but setting this up or rather how to needs HuGe amounts of work. 
 
 My attention so far is to get a working gui desktop and then look into setting up and running a GNU/hurd web server for the hell of it. 
 
 Im going to look into the net install as it looks more promising.

---

### Post by markharding557 on 2008-05-01
this is a kind of specialist thing so i reckon the folks at [http://forums.debian.net/]("http://forums.debian.net/")can help you better

---

### Post by Omnios on 2008-05-01
Finally getting somewhere. Used the lx install cd with the script to install. Then ran the install and gui script on the debian cd with a good apt source in the sources list. This took the lx install and loaded hopefully most of the stuff that was missing, what a hack job lol. Also my first try I got fraged on the upgrade and dist -upgrade so I used this to fix lic0.3 [http://lists.debian.org/debian-hurd/2007/09/msg00007.html](http://lists.debian.org/debian-hurd/2007/09/msg00007.html) . After breaking last time I did apt-get update but left the expert parts that uninstalled core parts that reuired Do, as I say! for the input and upgrading every thing else. After that started running upgrade and seems its intalling the core parts that it was going to uninstall. 
 
 At this point got gpg errors so tried wget to get keys and still nota, anyways got to the point whee the gpg error stoped posting on looking up the source list and got gpgv error at the end, being the *** I am I tried apt-get install gpgv and problem solved. 
 
 Looking pretty good so far but am now trying to get a gui desktop which seems limited and gnome and kde do not work yet. However these are listed as candidates. 
 
> 
**Selecting & Configuring Packages **

The x-window-system-core package brings you most of what you need for a base, plus you need to choose a window manager:
[LIST]
[*]WindowMaker, wmaker
[*]FVWM, fvwm
[*]Blackbox, blackbox
[*]TWM, twm
[/LIST]I know that Window Maker works, however, I cannot attest to the others. xfce4 might be temporarily broken.

 
 I want to try somthing straight forward or rather easy so if x is proken I do not mistake it as a wm problem. 
 
 Any suggestions. 
 
 A wm is not mission critical as after I get a desktop so I can say I did I am going to set up a web server for the hell of it. 
 
Also thank you Ubuntu and Ubuntu community as the only way I was able to get this far so far is from what I have learnt here!

---

### Post by SunnyRabbiera on 2008-05-01
well why bother though, HURD has not really gone anywhere in a while and good luck getting stuff to work in it...

---

### Post by Omnios on 2008-05-03
> **SunnyRabbiera said:**
> well why bother though, HURD has not really gone anywhere in a while and good luck getting stuff to work in it...

 Hi k finally took a break from hurd and installed Ubuntu 8.04 and it looks sweet;

 > 
why bother

  
 Hurd is not my desktop or os right now, its my toy.

 > 
good luck getting stuff to work in it


 This is probably why I want to play with it as a toy.

  Anyways once I get a running desktop running probably wont play with it much as its on a partition on my old tower which is now my fileserver.

 If I find a cheap old box or rambus ram for a gutted box I might play with it a bit more. 

 I read a lot online about how its not working for people and that and knowing myself that is probably the reason I feel driven to play with it. 

 Now as a desktop it might now seem anyething special but I gought thinking and was wondering if it has potential in specialized fields such as fly by wire flight computers for airliners and other mission critical systems if it can survive and recover from errors that would kill other kernels. 

 For example have the interpreters and server layers able to ident a hardware flaw and automaticly switch to backup of that specific hardware, Now exectly sure but it may have advantages for robotics and other applications. Sort of like a robotic calibration hardware layer that is part of the process rather than a programed part.. Also this could allow for things like artificial arms with pressure sensors build into the hardware level and work outside of a normal run root.

 Anyways bottom line do I care? not really, But what the hell.

---

### Post by xirtus on 2009-01-17
man why you gotta be  negative nancy like that? Linux sminuch... taste the kool-aid

---

