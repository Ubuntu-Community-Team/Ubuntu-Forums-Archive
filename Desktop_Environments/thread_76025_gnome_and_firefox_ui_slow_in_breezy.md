---
title: "gnome and firefox ui slow in breezy?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by jimmyp on 2005-10-14
Is anyone noticing that the gnome and firefox ui lags a bit every once in a while (once a minute or so)?  like, I go to the System menu, scroll over preferences on the way to administration but once the mouse is on administration, the preferences submenu stays up for 3/4 of a second or so... firefox does similar things, has anyone noticed this?

I'm running breezy with a geforce 3.  I'm using the nvidia drivers via the packages
nvidia-kernel-common
nvidia-glx
and updated my xorg.conf file to use the nvidia driver instead of nv.
My machine is a p4 2.2 w/512mb ram.

Is anyone else seeing similar lag?

---

### Post by jimmyp on 2005-10-14
No one else is seeing this?

---

### Post by erikpiper on 2005-10-14
Nope. Hoary did, and was all around slower. Breezy rocks!

IBM T23
1.2 Ghz P-III
512 MB RAM
Horrible graphics card.

---

### Post by spooky-mac on 2005-10-14
Sometimes my laptop shows some minor lags for no apparent reason. I don't know if this is related to a Breezy problem or if it is a dev-problem in Gnome. I thought it might be related to loading data from the harddisk, but that seems unrealistic...

---

### Post by bjourne on 2005-10-14
The delay in the top-left menus are very annoying. I don't think it is because Breezy got slower but instead it is some kind of coded delay to protect you from "mouse-slipping" and show the wrong menu. I think it works something like this: If you move the mouse cursor fast and a long distance (like 50 pixels) from where it were last, gtk thinks you slipped and will display the last menu for a little longer. Very annoying. I could be wrong though. 

Nautilus on the other hand, seems definitely to have gotten slower. :-(

---

### Post by bam on 2005-10-14
nope, nothin here, fast as ever...

---

### Post by fnando on 2005-10-14
I'm with the same problem.

I posted on [http://ubuntuforums.org/showthread.php?t=76214](http://ubuntuforums.org/showthread.php?t=76214)

ASUS P4S800
Pentium 4 3.0 HT
NVIDIA FX5200 128mb
512mb RAM
Ubuntu Breezy 2.6.12-9-386

I followed the steps below:
[http://ubuntuforums.org/showthread.php?t=75074#4](http://ubuntuforums.org/showthread.php?t=75074#4)

Maybe is something with NVIDIA drivers.... Any idea?

---

### Post by jimmyp on 2005-10-17
[QUOTE=fnando]I'm with the same problem.
Maybe is something with NVIDIA drivers.... Any idea?[/QUOTE]

I tried both the nv drivers and the nvidia drivers in the repository and both gave the same behavior.  Since firefox is slow too I'm thinking it's something wrong with gtk (does firefox use gtk?).  It is very annoying and I might have to resort switching distros :(

Something I haven't tried yet is installing the latest nvidia drivers from the nvidia website.  I highly doubt that will have any effect since the desktop is slow with both nv and nvidia drivers.  What kernel are you using?  I'm using  2.6.12-9-386.  I might try the -686 but doubt that will fix things either.

---

### Post by docomo on 2005-10-17
[quote=jimmyp]like, I go to the System menu, scroll over preferences on the way to administration but once the mouse is on administration, the preferences submenu stays up for 3/4 of a second or so... [/quote] 
I can reproduce this exact thing.

In general, I percieve Breezy to be slightly more snappy than Hoary though.

---

### Post by jimmyp on 2005-10-17
[QUOTE=docomo]I can reproduce this exact thing.

In general, I percieve Breezy to be slightly more snappy than Hoary though.[/QUOTE]

What video card, video drivers and kernel are you using?  Do you remember if this kind of thing happened right when you installed breezy or sometime after?  I don't remember when it started to happen to me (if it doesn't happen immediately after the initial install, but after we mess with packages and stuff then one could theoretically track down which package causes this problem).  Also, does the firefox ui seem to move slowly for you as well?

I jumped from debian so I can't compare to hoary.

Thanks for the confirmation, I might file a bug report.

---

### Post by bvc on 2005-10-18
[QUOTE=jimmyp]Since firefox is slow too I'm thinking it's something wrong with gtk (does firefox use gtk?).  It is very annoying and I might have to resort switching distros :( [/QUOTE]Firefox uses gdk not gtk. Before breezy was released, I found it a lot slower, and found cairo-1.0.0 (aa font rendering) to be the prob. I upgraded to cvs cairo and all is well. Firefox is just firefox and has increasingly became slower and slower, even with official firefox tarballs. Epiphany and Galeon won't do ya wrong.

---

### Post by docomo on 2005-10-18
[quote=jimmyp]What video card, video drivers and kernel are you using? Do you remember if this kind of thing happened right when you installed breezy or sometime after? I don't remember when it started to happen to me (if it doesn't happen immediately after the initial install, but after we mess with packages and stuff then one could theoretically track down which package causes this problem). Also, does the firefox ui seem to move slowly for you as well?

I jumped from debian so I can't compare to hoary.

Thanks for the confirmation, I might file a bug report.[/quote] 
Radeon 9600 with the flgrx driver. Kernel 2.6.12-9-k7. No, I don't notice slowness in firefox. 

I just upgraded from Hoary so I think this issue has been there since then. I probably wouldn't have thought much about it if I hadn't seen your post. I seem to remember there was some slowness in the panel menus in Hoary as well that I assumed was related to loading the icons (just like the program menu in windows xp can lag, especially if you have a lot of stuff in it).

The lag in going from "preferences" to "administration" specifically seems a bit exessive though (a second or so) and it can happen even if I used the same menus just 10 seconds ago so they should still be in RAM one would assume, and not have to be loaded from the hd.

---

### Post by nrgtek on 2005-10-18
I am getting that "choppy" lag on everything in breezy now, hoary was fine. When switching desktops, opening menu's, and using applications. It's an anoying 1 second delay of "drawing" the window. I'm using the linux-k7 kernel on my AMD XP-M laptop it's using an ATI 320M video card. 

I'm prolly going to go back to Hoary...any ideas? :confused:

---

### Post by jimmyp on 2005-10-18
Bug filed:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18058](https://bugzilla.ubuntu.com/show_bug.cgi?id=18058)

When did you upgrade to cairo cvs?  My machine has cairo 1.02 (released Oct 3) on it.

It is weird that firefox isn't slow for everyone that has this bug.  It is faster for me to rdesktop onto my windows laptop (1.7 ghz) and use firefox there than to use the one that came with ubuntu.

---

### Post by bvc on 2005-10-19
1.0.0 was the slow version. I got cvs around the middle of Sept. I haven't upgraded to 1.0.2 yet but I'd think the speed increases would still be there and you'd be fine. Are you using a svg icon theme? If so, are the icons used in the menu vacuumed? Inscape>File>Vacuum Defs (watch the statusbar to see if anything is removed)
Makes a big diff in size/performance/resource usage.

I'm even using clearlooks-cairo and all is well.
AMD Athlon(tm) XP 1900+
GF 440mx agp 64mb
NVIDIA Kernel Module  1.0-7174 (old)
Kernel:         2.6.10-5-386 (old)
512mb ram

I uninstalled firefox. Mozilla is a lot faster. I use Epiphany on a daily basis again as I did 10 months ago before switching to ff for whatever stupid reason, oh yeah...themes. I'd rather do w/o themes, which made ff even slower anyway.

---

### Post by majed on 2005-10-19
i installed firefox from mozilla.org and it works much faster than the ubuntu packaged version of firefox.. much faster!!! it doesn't hang.. and all works fine.. flash plugin was installed directly by firefox plugin wizard and i managed to get java plugin working and now its all good :)))

---

### Post by .Danny on 2005-10-19
It's slow for me as well.

majed, did you install the 1.5 beta 2 or some other version? I've installed the 1.5 beta 2 and flash is not working, altough it is a little faster.

[edit] Epiphany is working so incredibly fast, but without a good way to manage cookies and Adblock it's not of much use to me.

---

### Post by majed on 2005-10-19
Lord, no.. i installed 1.0.7. I tried the beta and it felt really beta and so i thought i can wait with the stable version as its working fine with me :)

---

### Post by jimmyp on 2005-10-19
Looks like Bjourne was right.  The ubuntu guys said that the lag is not a bug but was put there intentionally.  So I guess my only problem is firefox slowness, which has been documented and griped about in other threads.

---

### Post by .Danny on 2005-10-19
[QUOTE=jimmyp]Looks like Bjourne was right.  The ubuntu guys said that the lag is not a bug but was put there intentionally.  So I guess my only problem is firefox slowness, which has been documented and griped about in other threads.[/QUOTE]
It has been put there intentionally? o_O Can you tell me where they said that? And is there a way to remove it?:mad:

---

### Post by jimmyp on 2005-10-19
[QUOTE=Lord Death]It has been put there intentionally? o_O Can you tell me where they said that? And is there a way to remove it?:mad:[/QUOTE]

They said it here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=18058](https://bugzilla.ubuntu.com/show_bug.cgi?id=18058)

I don't know how to remove it.

---

