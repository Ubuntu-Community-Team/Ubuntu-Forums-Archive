---
title: "Debian/Ubuntu Doomsday Packages"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by Yagisan on 2005-12-30
*Please note this is a continuation of a thread originally started here [http://www.ubuntuforums.org/showthread.php?t=51241](http://www.ubuntuforums.org/showthread.php?t=51241) I've decided to post this here as packages are no longer available for hoary, only breezy.

Been a while since the last update, so what's new:

recent changes and additions include:
[LIST]
[*]Packaged the et style hud face for doom
[*]Edited and packaged the johnx fluids pack. This pack now works with all currently packaged pwads and megawads, including icarus with high-res textures and no corruption.
[*]Packaged kurikai's doom lights
[*]Packaged kurikai's doom rain - looks very good in doom 1, I'd highly recommend it.
[*]Packaged an updated version of kurikai's lava lights. No longer causes the pc to crash on levels with lots of lava, I'd highly recommend it.
[*]Packaged sycraft's high quality doom music. Currently when enabled this replaces all music, even music in pwads.
[*]Packaged picklebro's telports for heretic.
[*]Packaged sycraft's high quality heretic music. Currently when enabled this replaces all music, even music in pwads.
[*]Packaged the heretic walllight effects found at jfiles
[*]Updated the doom texture pack to include all Doom. Doom 2 and Plutonia textures released at jfiles
[*]Packaged the hexen lightmaps found at cains website
[*]Packaged the hexen lights found at cains website
[*]Packaged sycraft's high quality hexen music. Currently when enabled this replaces all music, even music in pwads.
[*]Packaged the hexen textures found at cains website, with any missing textures from the jxtp at jfiles.
[/LIST]
Future plans are to, in no particular order
[LIST]
[*]Rework the sycraft music packs to disable them for pwads with custom music.
[*]Get the 32bit compatiblity package for amd64 to run with sound instead of crashing, so I can release a package on amd64, before a native amd64 package is ready. The 32bit compatiblity package already runs without sound, but dies a horrible death when sound is enabled.
[*]Make timidity a depends for music, and for all music to be rendered by timidity.
[*]Package a decent patchset for timidity, such as fluid.
[*]Fix the broken Debian autobuilders so I can update the Debian repository.
[*]Make a server only package of deng.
[*]Merge the wad installer packages into the main deng package.
[*]Package some more pwads.
[/LIST]

In the outlook ahead, I don't expect any major changes to the packages until the next jDRP release, which will obsolete several existing packages. Packages are always only built for the current stable release of Ubuntu and Debian respectivly. Approximately 1 month after a new stable release of the distro, the old repository will be deleted.

Feel free to request other resources packs to be packaged, and if possible I will package them. Any other comments about the packages, feel free to comment here.

Regards, and Happy New Year.

Yagisan

---

### Post by Greg2 on 2006-02-27
[QUOTE=Yagisan] I've decided to post this here as packages are no longer available for hoary, only breezy.[/QUOTE]
Hello Yagisan,

I've been to your site and followed the instructions for adding your repository. I've installed deng and the deng-iwad-doom2-installers without any problems... and they work great.

The problem I have is when I try to install deng-jdoom-rp-core (or any of the effects), I receive this error:```
W: Failed to fetch [http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/multiverse/binary-all/games/deng-jdoom-rp-core_20051128-ubuntu1_all.deb](http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/multiverse/binary-all/games/deng-jdoom-rp-core_20051128-ubuntu1_all.deb)
  301 Moved Permanently
```it would appear that I'm being redirected to the hoary repository?

My sources.list:```

-snip-
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
```I can d/l these and manually install them, but I thought I would let you know first.

Thanks for all the great work you've done on this! :D

---

### Post by Yagisan on 2006-02-28
[QUOTE=Greg2]Hello Yagisan,
The problem I have is when I try to install deng-jdoom-rp-core (or any of the effects), I receive this error:```
W: Failed to fetch [http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/multiverse/binary-all/games/deng-jdoom-rp-core_20051128-ubuntu1_all.deb](http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/multiverse/binary-all/games/deng-jdoom-rp-core_20051128-ubuntu1_all.deb)
  301 Moved Permanently
```it would appear that I'm being redirected to the hoary repository?[/QUOTE] I was making some changes to the server last night and made a typo on the redirects :oops: I fixed it today so it should be ok now.

---

### Post by Greg2 on 2006-02-28
It’s working now.

Thanks again for all the work you’ve put into making this so easy to install and play. The last couple of times I set this up... well, it was a ‘bit’ more difficult to do. :)

---

### Post by david_e on 2006-03-03
I don't know if this is a bug or if it's a problem with my video card...

I have already sent a bug report, but I would like to know if someone else had this problem and if there is a solution: the game runs without any wall texture... I can only see monsters! It's like walking outside the level with the IDCLIP (in the old original Doom)...

I have tried doomsday with the originals doom2 and heretic wads, but I have this problem with both them.

My computer is an Acer Ferrari 3000:

CPU : AMD Athlon XP 2500+
RAM : 512 Mb
VIDEO : ATI Radeon 9200 128Mb 

Drivers:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1030 (X4.3.0-8.20.8)

```

Followed this HOW-TO to install them:

[http://ubuntuforums.org/showthread.php?p=423584#post423584](http://ubuntuforums.org/showthread.php?p=423584#post423584)

---

### Post by Yagisan on 2006-03-04
[QUOTE=david_e]I don't know if this is a bug or if it's a problem with my video card...

I have already sent a bug report, but I would like to know if someone else had this problem and if there is a solution: the game runs without any wall texture... I can only see monsters! It's like walking outside the level with the IDCLIP (in the old original Doom)...[/quote]
Sadly, you are not alone. I have had a few reports like this, and have forwarded them upstream. The only thing that they had in common, was that the all used ATI graphics cards. I purchased a Radeon 7200 on ebay to see if I could reporoduce it, but have been unsuccessful. I suspect it is an interaction between the drivers, and the opengl engine for the game.

Something you might want to try is to edit the startup options for doom2.
In a terminal type:
```
gksudo gedit /usr/share/applications/deng-iwad-doom2-installer.desktop
```
Delete -anifilter and -texcomp. Save then try again.

Regards,
Yagisan.

---

### Post by david_e on 2006-03-05
Thanks for the reply... I have tried removing -anifilter and -texcomp from:

```
/usr/share/applications/deng-iwad-doom2-installer.desktop
```

but it didn't work. 

I have also tried playing the win version of dommsday with wine, but it seems that doomsday doesn't run under wine...

---

### Post by mike998 on 2006-03-05
Just wanted to post to say thanks.
This works perfectly with my doom2 wads.
I even installed all the extra stuff (graphics and sounds) and it's great!:)

---

### Post by Yagisan on 2006-03-06
[QUOTE=david_e]Thanks for the reply... I have tried removing -anifilter and -texcomp from:

```
/usr/share/applications/deng-iwad-doom2-installer.desktop
```

but it didn't work. [/quote]
Sorry to hear that :( There is some major code refactoring going on in beta4 at the moment. As soon as it is released I'll package it and we can try again.

[QUOTE=david_e]I have also tried playing the win version of dommsday with wine, but it seems that doomsday doesn't run under wine...[/QUOTE]I tried that too. It also doesn't work under vmware (graphical errors galore)

[QUOTE=mike998]Just wanted to post to say thanks.
This works perfectly with my doom2 wads.
I even installed all the extra stuff (graphics and sounds) and it's great!:) [/quote] Glad to hear it works for you. Nvidia user ? You must have a **lot** of patience to download the addons. I know my link isn't very fast.

---

### Post by david_e on 2006-03-24
Finally I was able to fix the problem!

As I said I had installed my video drivers following:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

I have tried reinstalling them following these instructions:

[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

and now everithing is working fine!!!!

I really don't know why this game now runs because I still know little about Linux word (even if I have not win any more on my pc)....

Hope this will help others with the same problem!

PS: Sorry for my English...

---

### Post by mike998 on 2006-03-24
Glad to hear it works for you. Nvidia user ? You must have a **lot** of patience to download the addons. I know my link isn't very fast.[/QUOTE]

Uhhh nope...  To be honest, there's a few problems with the speed slowing down occasionaly and the sky goes a little nuts, but there again - 
```
[4294689.567000] agpgart: Detected an Intel 855 Chipset.
[4294689.567000] agpgart: Detected 892K stolen memory.

```
The video on this laptop isn't exactly top of the range :-D 
I **am** patient and it was very much so worth the wait.
Again, good work and thanks!

---

### Post by Yagisan on 2006-03-25
[QUOTE=mike998]Uhhh nope...  To be honest, there's a few problems with the speed slowing down occasionaly[/quote]I've also noticed them on my dev box. It tends to happen with either lots of pickups or enemies and model packs on. I suspect it has to do with the fact that all 3d rendering is cpu based, and that doom wasn't designed to have masses of 3d models charging down at you. I'm hoping beta4 improves that, and the new model packs in production should also help.

[QUOTE=mike998]and the sky goes a little nuts[/quote] Usually that seems to be caused by errors in the wad file itself (even ids wads too). Does it look like a hall of mirrors ?

[QUOTE=mike998]I **am** patient and it was very much so worth the wait.
Again, good work and thanks![/QUOTE]Your quite welcome. I also post future plans over here [http://deng.sourceforge.net/blog/](http://deng.sourceforge.net/blog/) so you may want to check it out to get an idea of what's comming up.

---

### Post by KingBahamut on 2006-03-25
You are the man Yags. 

Did you ever get your Linspire woes worked out?

---

### Post by Yagisan on 2006-03-26
[QUOTE=KingBahamut]You are the man Yags. 

Did you ever get your Linspire woes worked out?[/QUOTE]
No. Linspire is still offering doomsday through CNR. The claim it is free, after you pay for CNR. Hence, you need to pay for doomsday, which is in violation of the license. I do note however, they are using a version that predates any of my copyright though (my copyright begins in the 1.9.0 packages, where I create installers, a lancher wrapper, and man pages.)

---

### Post by squizzi on 2008-03-22
Woops.

---

### Post by zergling on 2008-05-14
Hi Guys,
I just put in my repositories 

-snip-
deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse

but I can not see doomsday, what should I do?
I am using Ubuntu 8.04.

Another question, I have also tried to compile doomsday from the source, but when I run make I get this error.

> 
[  0%] Built target Generate.pk3
[  1%] Building C object CMakeFiles/doomsday.dir/engine/portable/src/bsp_intersection.o
In file included from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/p_mapdata.h:41,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/edit_map.h:31,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/de_edit.h:33,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/bsp_main.h:37,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/de_bsp.h:31,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/src/bsp_intersection.c:34:
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/rend_bias.h:92: warning: &#8216;struct rcolor_s&#8217; declared inside parameter list
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/rend_bias.h:92: warning: its scope is only this definition or declaration, which is probably not what you want
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/rend_bias.h:92: warning: &#8216;struct rvertex_s&#8217; declared inside parameter list
In file included from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/bsp_node.h:38,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/de_bsp.h:34,
                 from /home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/src/bsp_intersection.c:34:
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/bsp_intersection.h:69: warning: &#8216;struct bspartition_s&#8217; declared inside parameter list
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/src/bsp_intersection.c:231: error: conflicting types for &#8216;BSP_IntersectionCreate&#8217;
/home/zergling/Desktop/deng-1.9.0-beta5.1/doomsday/engine/portable/include/bsp_intersection.h:69: error: previous declaration of &#8216;BSP_IntersectionCreate&#8217; was here
make[2]: *** [CMakeFiles/doomsday.dir/engine/portable/src/bsp_intersection.o] Error 1
make[1]: *** [CMakeFiles/doomsday.dir/all] Error 2
make: *** [all] Error 2


I checked already on the net, but I could not find any solution :(.
I hope someone is able to help me.
Bye for now and take care :)

P.S. Does any of you has the deb file?

---

### Post by DoktorSeven on 2008-05-14
I only have a debian package for the "stable" version of Doomsday (1.8.6) which I use over the latest versions due to it, well, being more stable for me.  (It's [on this site](http://sdcofer.googlepages.com/), as well as a simple GUI launcher program.)

---

### Post by zergling on 2008-05-15
> **DoktorSeven said:**
> I only have a debian package for the "stable" version of Doomsday (1.8.6) which I use over the latest versions due to it, well, being more stable for me.  (It's [on this site](http://sdcofer.googlepages.com/), as well as a simple GUI launcher program.)

I did it!
Thank you so much :)
Every time I play Doom, I will think about you :D
Ciao!

---

### Post by disturbedite on 2008-05-15
it seems like ages, and i *mean ages* since a new version of doomsday was released.

---

### Post by DoktorSeven on 2008-05-15
> **disturbedite said:**
> it seems like ages, and i *mean ages* since a new version of doomsday was released.

They're in 1.9.0 development, erm, "heck", it seems :)

It seems like they tried to change a lot of things and in the process a ton of bugs have been introduced.  Not blaming them at all, in fact, the new version looks very promising, but it's just too unstable for my day to day play of DOOM (and yeah, I play it nearly daily it seems).

1.8.6 may be obsolete, but at least it works.

---

### Post by disturbedite on 2008-05-15
heh, yeah, it sure has been in development "heck". ;)

---

### Post by DoktorSeven on 2008-05-15
Well, it's a family forum, I didn't want to say the other word. ;)

---

### Post by disturbedite on 2008-05-16
> **DoktorSeven said:**
> Well, it's a family forum, I didn't want to say the other word. ;)
thats what i figured.

# god forbid we should use the "H" word when talking about doom! :lolflag:

---

### Post by obsrv on 2008-07-20
Repositories no longer work. Is there any alternatives?

---

### Post by DoktorSeven on 2008-07-20
> **obsrv said:**
> Repositories no longer work. Is there any alternatives?

Check my post above for [this link](http://sdcofer.googlepages.com/) to a 1.8.6 package (no 1.9.0 betas, I explain why above).

---

