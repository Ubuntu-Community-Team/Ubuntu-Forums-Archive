---
title: "[SOLVED] Does anybody here use AdvanceMAME?"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2007-06-09
I'm still finding my way around Linux, but so far have been a little scared of using the terminal. I bought a Linux magazine recently (Linux Format, very good!) and in it there was a small guide to installing .tgz files. Well, I thought, now's my chance....

I've been looking for a good MAME, and saw that AdvanceMAME was a .tgz file, so I gave it a go. Followed the instructions closely. It took a good 30 mins for my PC to "build" the program, but all seemed to go well, and make install went fine. Except, I don't know how to use it now. I've read the readme's and text files, but I'm none the wiser really. I don't even know where it is! If there is anyone here with experience of this program I'd be very grateful. I downloaded it from [here.]("http://advancemame.sourceforge.net/")

Plus, is there a way of removing this if I can't get my head around it? I'd rather give it a good go, but if I have to remove it I'd appreciate your guidance. 

Many thanks. Sorry for my noobish question. :redface:

---

### Post by jim_p on 2007-06-09
I had the same problem. I downloaded and compiled it and all i got was a new command like "advmame" from the terminal. I suppose it is used like mplayer's 

```
"mplayer videofile.avi -option1 -option2"
```

The site does have something that looks like an graphical interface to me, Advanced Menu, but i have no idea how to re-compile the whole thing using the Advanced Menu sources.

When it comes to uninstall it, you have to run 

```
./make uninstall
```

from the same directory you used to compile and install the program. You also have to remove some folders like "snapshot, roms, etc" from your HOME directory.

---

### Post by BigSilly on 2007-06-10
> **jim_p said:**
> 
The site does have something that looks like an graphical interface to me, Advanced Menu, but i have no idea how to re-compile the whole thing using the Advanced Menu sources.

When it comes to uninstall it, you have to run 

```
./make uninstall
```

from the same directory you used to compile and install the program. You also have to remove some folders like "snapshot, roms, etc" from your HOME directory.

Many thanks for your reply. That's exactly what threw me out too. I saw the screenshots on their site, and they feature a GUI like you say. The readme's and text files are really made for experienced Linux users, so I can't make head nor tail of them. I'm trying to get to grips with the command line, but it's early days and I think I picked the wrong program to learn with!

I can't seem to uninstall it either. I downloaded the .tgz to a folder on my desktop I created (My Downloads), and compiled it from there. When I try to remove it, it can't do it. It says "./make no such file or directory".

Ah well, thanks again for your help. :)

---

### Post by gigaferz on 2007-08-28
yeah,dont you hate that?

---

### Post by BigSilly on 2007-08-28
Nah, I've figured out how to use it now. It's pretty cool actually, but it could do with a good GUI. Nevertheless, I can use it fine as is. Nice one!

---

### Post by po0f on 2007-08-28
BigSilly,

I've found arcade emulators to be too much of a pain to set up under Linux.  Why can't I compile a package from source, point it to a directory of ROMs, and double-click and play?

---

### Post by BoyOfDestiny on 2007-08-28
> **po0f said:**
> BigSilly,

I've found arcade emulators to be too much of a pain to set up under Linux.  Why can't I compile a package from source, point it to a directory of ROMs, and double-click and play?

I had used advancemame and advancemenu (the gui front-end for it). However, advmame is no longer being updated so I switched to sdlmame

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

If you need more
Wahcade seems like a good front-end
[http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

Hopefully these will give you an easier time. 

For SDLMAME, extract it, compile it,
then run
./mame -createconfig

edit the ini file to point to your roms

then

./mame

Anyway, I want to see the emulation scene to continue to improve under Linux. So far I have to say not bad ;)

:guitar:

---

### Post by gigaferz on 2007-08-28
actually there is!!::: advanceMenu, wich i tried compiling and check installing, and there is somekind of bug spent 3 hours...well,, at least There are more oprtions...

---

### Post by tom-ubuntu on 2007-08-29
Nice to see that other Ubuntu-Users are interested in MAME /Arcade games aswell. Haven't done anything lately, but played around with AdvanceMame aswell long time ago, but was not successful in getting it up and running under Ubuntu.

Would be great, if you guys could build a deb package for easier use. I am sure, others would be interested in it as well.

---

### Post by po0f on 2007-08-29
tom-ubuntu,

[Click](http://apt.ludomatic.fr/?hl=en).

---

### Post by tom-ubuntu on 2007-08-30
Thank you very much. Will check it out.

---

### Post by BigSilly on 2007-08-30
I'm going to check that out too. Thanks for that. Is it safe to use that as a repository then? Sorry if that's a silly question, but I'm still using only approved Ubuntu sources at the moment, and this will be new to me.

---

### Post by po0f on 2007-08-30
BigSilly,

AFAIK it's safe.  The one time I tried to set up SDLMAME on my box, I used that repo.  You will still need a front-end program for it if you don't like the command line for launching all your games.

---

### Post by mahalos on 2007-08-31
i installed the latest SDLmame using this guys .Deb

[http://wallyweek.altervista.org/]("http://wallyweek.altervista.org/")

give it a go

---

### Post by BigSilly on 2007-09-02
> **mahalos said:**
> i installed the latest SDLmame using this guys .Deb

[http://wallyweek.altervista.org/]("http://wallyweek.altervista.org/")

give it a go

You, sir, are an absolute bloody star! I've downloaded this, and it works beautifully. I'll leave this chap some feedback, but so far this works amazingly on my Ubuntu, and just has to be put into the repos.

My heartfelt thanks for this. You have made my day, nay year!

---

### Post by BigSilly on 2007-09-03
Hoo boy, I never thought I'd ever see Street Fighter 3 Third Strike running on Linux! But run it does and it's excellent - really fast with no lag or anything. This is an excellent MAME package. 

I've emailed whoever is responsible just to say thanks. And thanks again to mahalos and the Ubuntu forums. I honestly didn't expect to play MAME ever again as a Linux user, certainly not an up to date one like this. Toppermost banana! :D

---

### Post by Elohim on 2007-09-03
> **mahalos said:**
> i installed the latest SDLmame using this guys .Deb

[http://wallyweek.altervista.org/]("http://wallyweek.altervista.org/")

give it a go

That would be my suggestion too :)  I use SDLMame, and use Wahcade as a front end.  Works great!

---

### Post by BigSilly on 2007-09-03
Funnily enough, I downloaded the .deb from Wahcade's site and installed it, but it didn't work for me. All I got when I tried to run it (from my Games menu) was a white screen, and I could just about make out some lettering but it was too indistinct to understand what was going on. If anyone here has a clue what has gone wrong here and knows what to do I'd be most grateful. I did try removing it and re-installing it, but the same thing happened.

Luckily though, sdlmame's own menu is more than up to the job. It's got everything you would need really. I heartily recommend wallyweek's site for this. I hope this will work on Gutsy Gibbon when the time comes too. Is it likely that these older .deb files will still run on a newer Ubuntu, or will I have to get an upgraded mame?

---

### Post by Elohim on 2007-09-03
> **BigSilly said:**
> Funnily enough, I downloaded the .deb from Wahcade's site and installed it, but it didn't work for me. All I got when I tried to run it (from my Games menu) was a white screen, and I could just about make out some lettering but it was too indistinct to understand what was going on. If anyone here has a clue what has gone wrong here and knows what to do I'd be most grateful. I did try removing it and re-installing it, but the same thing happened.

Luckily though, sdlmame's own menu is more than up to the job. It's got everything you would need really. I heartily recommend wallyweek's site for this. I hope this will work on Gutsy Gibbon when the time comes too. Is it likely that these older .deb files will still run on a newer Ubuntu, or will I have to get an upgraded mame?

SDLMame's own menu?  I didn't think it had a front-end?

---

### Post by DoktorSeven on 2007-09-04
SDLmame now has an internal menu that runs inside the window (similar to how old versions of MAME had menus you could bring up for configuration purposes).

Last time I tried it though, it kept crashing on me.  Maybe they've improved it since.

---

### Post by BigSilly on 2007-09-04
Ah I see. Well, it works just fine for me luckily, and puts an extra bit of polish on the package I reckon. I was running it from the terminal at first, which was fine too, but having a neat menu wraps it all up nicely. 

Please do give this a shot if you're a retro nut. You'll love it. :D

---

### Post by DoktorSeven on 2007-09-04
Yeah, I just built it again and am having the same issues; random segfaults and occasional sound issues (as in no sound when I start another game from the menu when there was sound in the game before, and sound when I restart SDLmame).

Seems rather buggy to me, though I guess it's the latest option for MAME since xmame is stuck at .106.  Works fine but doesn't have the new stuff.

---

### Post by BigSilly on 2007-09-04
Have you tried the .deb at wallyweek? Is this the version you are referring to? I don't understand how it can be fine on my PC but not on yours! Let me know.

---

### Post by Elohim on 2007-09-04
> **DoktorSeven said:**
> SDLmame now has an internal menu that runs inside the window (similar to how old versions of MAME had menus you could bring up for configuration purposes).

Last time I tried it though, it kept crashing on me.  Maybe they've improved it since.

Is this a menu that is capable of finding all the games you have, and allow for selection?  That is what I'm thinking of as a front-end, like Wahcade.  At any rate, I prefer Wahcade, but if you could post a screenshot, or a link to what SDLMame has, that would be great :)

---

### Post by Elohim on 2007-09-04
> **BigSilly said:**
> Have you tried the .deb at wallyweek? Is this the version you are referring to? I don't understand how it can be fine on my PC but not on yours! Let me know.

That is what I installed, and it works fine for me.

---

### Post by DoktorSeven on 2007-09-04
Mine's compiled from source.  It's possible that the optimizations could be affecting the binary, so I will go back and recompile with the optimizations turned down.

Edit: same deal.  For the curious, this is the output that sometimes occurs when starting a game.  There's no pattern, and a game that will start fine sometimes and give this crash other times.

```

$ ./mamepp 
*** glibc detected *** ./mamepp: free(): invalid next size (fast): 0x0a87d908 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7ce07cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7ce3e30]
./mamepp[0x8fea325]
./mamepp[0x8fea317]
./mamepp[0x8fea317]
./mamepp[0x89c0ff7]
./mamepp[0x89b4f5a]
./mamepp[0x89ead53]
./mamepp[0x89a43c9]
./mamepp[0x8941b35]
./mamepp[0x8914b8b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7c8eebc]
./mamepp(realloc+0x5d)[0x804ab91]
======= Memory map: ========
08048000-09c83000 r-xp 00000000 03:02 216397     /home/stephen/src/sdlmame0118u4/mamepp
09c83000-09d65000 rw-p 01c3a000 03:02 216397     /home/stephen/src/sdlmame0118u4/mamepp
09d65000-0aa70000 rw-p 09d65000 00:00 0          [heap]
b575b000-b5766000 r-xp 00000000 03:02 131136     /lib/libgcc_s.so.1
b5766000-b5767000 rw-p 0000a000 03:02 131136     /lib/libgcc_s.so.1
b5832000-b5833000 ---p b5832000 00:00 0 
b5833000-b6033000 rwxp b5833000 00:00 0 
b6033000-b6034000 r-xp 00000000 03:02 1015990    /usr/lib/gconv/ISO8859-1.so
b6034000-b6036000 rw-p 00000000 03:02 1015990    /usr/lib/gconv/ISO8859-1.so
b6036000-b603d000 r--s 00000000 03:02 1016043    /usr/lib/gconv/gconv-modules.cache
b603d000-b603e000 rw-s 00000000 00:07 1812856841  /SYSV00000000 (deleted)
b603e000-b603f000 rw-s 00000000 00:07 1812824071  /SYSV00000000 (deleted)
b61d0000-b62d0000 rw-s d0114000 00:0c 15102      /dev/nvidia0
b62d0000-b62d1000 rw-s e0820000 00:0c 15102      /dev/nvidia0
b62d1000-b63d3000 rw-s d0011000 00:0c 15102      /dev/nvidia0
b63d3000-b68d3000 rw-s d8000000 00:0c 15102      /dev/nvidia0
b68d3000-b7120000 r-xp 00000000 03:02 737930     /usr/lib/libGLcore.so.1.0.9631
b7120000-b7155000 rwxp 0084d000 03:02 737930     /usr/lib/libGLcore.so.1.0.9631
b7155000-b7159000 rwxp b7155000 00:00 0 
b7159000-b715a000 ---p b7159000 00:00 0 
b715a000-b795a000 rwxp b715a000 00:00 0 
b7983000-b79e8000 rw-p 00000000 00:0c 2553       /dev/zero
b79e8000-b7a59000 r-xp 00000000 03:02 737905     /usr/lib/libGL.so.1.0.9631
b7a59000-b7a73000 rwxp 00070000 03:02 737905     /usr/lib/libGL.so.1.0.9631
b7a73000-b7a74000 rwxp b7a73000 00:00 0 
b7a74000-b7a78000 r-xp 00000000 03:02 738571     /usr/lib/libXfixes.so.3.1.0
b7a78000-b7a79000 rw-p 00003000 03:02 738571     /usr/lib/libXfixes.so.3.1.0
b7a79000-b7a81000 r-xp 00000000 03:02 738561     /usr/lib/libXcursor.so.1.0.2
b7a81000-b7a82000 rw-p 00007000 03:02 738561     /usr/lib/libXcursor.so.1.0.2
b7a88000-b7a8f000 r-xp 00000000 03:02 738591     /usr/lib/libXrender.so.1.3.0
b7a8f000-b7a90000 rw-p 00006000 03:02 738591     /usr/lib/libXrender.so.1.3.0
b7a9c000-b7a9d000 rw-s 81000000 00:0c 12146      /dev/snd/pcmC0D0p
b7a9d000-b7a9e000 r--s 80000000 00:0c 12146      /dev/snd/pcmC0D0p
b7a9e000-b7a9f000 rw-s 00000000 00:07 1812922379  /SYSV00000000 (deleted)
b7a9f000-b7ae0000 rw-s df7e9000 00:0c 15102      /dev/nvidia0
b7ae0000-b7ae1000 rw-s 1157b000 00:0c 15102      /dev/nvidia0
b7ae1000-b7ae2000 rw-s df829000 00:0c 15102      /dev/nvidia0
b7ae2000-b7ae6000 rw-s 15041000 00:0c 15102      /dev/nvidia0
b7ae6000-b7b0c000 rw-s 00000000 00:07 1790148608  /SYSV00000000 (deleted)
b7b0c000-b7b0d000 r-xp 00000000 03:02 967106     /usr/lib/tls/libnvidia-tls.so.1.0.9631
b7b0d000-b7b0e000 rw-p 00000000 03:02 967106     /usr/lib/tls/libnvidia-tls.so.1.0.9631
b7b0e000-b7b13000 r-xp 00000000 03:02 738589     /usr/lib/libXrandr.so.2.1.0
b7b13000-b7b14000 rw-p 00005000 03:02 738589     /usr/lib/libXrandr.so.2.1.0
b7b14000-b7b15000 rw-p b7b14000 00:00 0 
b7b15000-b7b22000 r-xp 00000000 03:02 738569     /usr/lib/libXext.so.6.4.0
b7b22000-b7b23000 rw-p 0000d000 03:02 738569     /usr/lib/libXext.so.6.4.0
b7b23000-b7b24000 rw-p b7b23000 00:00 0 
b7b24000-b7b28000 r-xp 00000000 03:02 738565     /usr/lib/libXdmcp.so.6.0.0
b7b28000-b7b29000 rw-p 00003000 03:02 738565     /usr/lib/libXdmcp.so.6.0.0
b7b29000-b7b2b000 r-xp 00000000 03:02 738554     /usr/lib/libXau.so.6.0.0
b7b2b000-b7b2c000 rw-p 00001000 03:02 738554     /usr/lib/libXau.so.6.0.0
b7b2c000-b7b3a000 r-xp 00000000 03:02 Aborted (core dumped)

```

---

### Post by IcKY99 on 2008-12-10
> **BigSilly said:**
> You, sir, are an absolute bloody star! I've downloaded this, and it works beautifully. I'll leave this chap some feedback, but so far this works amazingly on my Ubuntu, and just has to be put into the repos.

My heartfelt thanks for this. You have made my day, nay year!

I know this sounds stupid but i just installed it and its not showing up in my applications. I just installed Ubuntu last week, im a total linux n00b.

---

### Post by BigSilly on 2008-12-10
> **IcKY99 said:**
> I know this sounds stupid but i just installed it and its not showing up in my applications. I just installed Ubuntu last week, im a total linux n00b.

That's odd. SDLMame usually puts an entry in your Applications/Games menu. If not, just open a terminal and type in ```
sdlmame
``` This should start the program for you so you know it's working. You'll probably find it wants you to edit your mame.ini file to point it at your roms. You'll need to type into a terminal ```
sudo gedit /etc/sdlmame/mame.ini
``` then your password to edit it with your preferences. 

You can edit the menu to manually add a program icon, or I suspect that a reboot might just fix that on it's own. If not, right click on the Applications bar, and select edit menus. You can click the Games category, and manually add the New Item and the commands you need. The command you'll need is /usr/bin/sdlmame, and you can call it M.A.M.E, and perhaps add to the comments section Multiple Arcade Machine Emulator. I've attached a little MAME icon for you. It's the one I use myself. It's just a little .png, but it's ideal for the menu and the toolbar. Hope it's of some use to you.

Good luck!

---

### Post by snide_tripod on 2010-12-23
Hello.  Linux noob here.  I have run mame on my old computers under windows before, and thought that it would be great to have it on my xubuntu 10.10 system.  I downloaded the deb found at [http://sdlmame.wallyweek.org/download/](http://sdlmame.wallyweek.org/download/) and when the installer ran it printed an error message : [COLOR=Red]"Error: Breaks existing package 'mame-common' that conflict: 'sdlmame'. But the '/tmp/mame_0.140u1-0ubuntu1~ww1~maverick_i386.deb' provides it via: 'sdlmame'"[/COLOR].""  Help Pleeze.  Anybody!!


Well I searched a little more and found this web site with a deb.  [http://sourceforge.net/projects/gxmame/files/gxmame/0.35beta2/gxmame_0.35beta2-1_i386.deb/download](http://sourceforge.net/projects/gxmame/files/gxmame/0.35beta2/gxmame_0.35beta2-1_i386.deb/download).  I hope it works.

---

