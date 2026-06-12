---
title: "neverwinter nights under AMD64 Feisty"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by MelancholyStoo on 2007-05-17
I'm having problems running Neverwinter Nights (original version) under 64 bit Feisty.

I've tried downloading the binaries from the Bioware site and updated to the latest version (1.68 ), however when I try to execute ./nwn I get the message "Permission denied".  Running as Sudo makes no difference.  I also tried downloading [this script]("http://icculus.org/~ravage/nwn/") but when I tried running it, it gave the message 

```
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
Press Return to close this window...
```

I'm also aware that I need 32 bit libraries Ia32-lib which I seem to have from the Synaptic package manager.  Are there any extra packages that I'll need?

Cheers,

Stoo.

---

### Post by LuisGMarine on 2007-05-17
I'm going to attempt this as soon as I get my cd's back in ( just moved , still waiting for some of my things to arrive ).

I'll monitor this thread to see if you get it working on feisty AMD64, if not I'm going to try and see if I can get it running by myself and post a guide somwhere.  This is an awesome game and I can't wait to run it on AMD64.  I already have a general Idea of how to run it.

---

### Post by MelancholyStoo on 2007-05-19
Thanks for your comments LuisG, I hope you get your CDs back soon!!

Anyone else have any idea how to get Neverwinter Nights going?

---

### Post by LuisGMarine on 2007-05-19
I got it working ! 

A couple of things, what version do you have?  I have gold, so the install directions are sitting right here infront of me, at least the ones that I used and got the game working.

The game over here runs perfectly, although I could be lying since my manual got left back , and now I don't have the CD key to start the game.  Other than that the game installed fine, and runs well, the sound and image quality for what I"ve been able to see so far is outstanding.  Looks like its going to run very well on my system and I don't expect to see any problems.

So just post back on what version you have, so we can get started!  Hopefully you have the Gold version! :crosses fingers:

:lolflag:

---

### Post by MelancholyStoo on 2007-05-19
Sadly, I only have the standard version and not Gold.  But let me know what you did anyway, the info could still come in useful.  maybe....

---

### Post by LuisGMarine on 2007-05-19
Ok. the instructions might be a little bit different, but the overall directions should be quite the same.

First lets start with the libs.  I'm not 100% positive on what libs you might need, but this is just a few that I have downloaded, and I'm sure it can't hurt your system to get them either.  I used these libs for Doom 3, NWN, ET and soon UT 2004 and Cedega.

Here is the list, use apt-get, aptitude , or synaptic to install these packages.  Once again this might or might not affect the install, like I said, at one point or another I needed these libs for those games.

[LIST]
[*]ia32-alsa-oss
[*]ia32-libs
[*]ia32-libs-gtkglext1
[*]ia32-libs-gtk
[*]ia32-libs-sdl
[*]lib32asound2
[*]libc6-dev-i386
[*]lib32z1-dev
[*]lib32gcc1
[*]linux32
[/LIST]

Again, some of these libs you don't even need.  But for the purpose of trying to get the game to work with your computer I'm giving you all the 32-libs I have on my system.
[URL="http://nwn.bioware.com/downloads/linuxclient.html#lininstall"]
Click here to get the tutorial on installing NWN original on your Linux computer.[/URL]

I'll try to give you a rough picture of what you have to do, to me its quite simple, but just in case you might run into trouble.

_**Step 1:**_ Download the Linux Client Resources v1.29, then extract them , and it should create a directory for nwn, it will tell you where it created it too, I'm guessing by default it should create it in /home/username

_**Step 2:**_ Skip unless you need to install in a different language ( other than English )

**_Step 3:_** Create an account with Bioware to get the [COLOR="Blue"]Linux Client Binaries[/COLOR].

_**Step 4:**_ Once you have the [COLOR="Blue"]Linux Client Binaries[/COLOR], you need to cd 'change directory', into the nwn folder created by extracting the contents of Step 1 and extract the [COLOR="Blue"]Linux Client Binaries[/COLOR] there.

For example:

Lets say the extraction of Step 1 creates a directory under */home/username/nwn*
```
cd /home/username/nwn
```
Then you need to extract the [COLOR="Blue"]Linux Client Binaries[/COLOR] in here, so to do that run this:
```
tar -xzvf /path/to/linux-client-binaries.tar.gz
```
Of course substituting the */path/to/linux-client-binaries.tar.gz* with the actual path to the [COLOR="Blue"]Linux Client Binaries[/COLOR].

_**Step 5:**_ Requires you to update the game, I'll fill you in on this later since I'm about to do it in a second after I'm done with this post.

_**Step 6:**_ Play that game kid!

Anyhow that's a down 'n dirty quick look into installing it.  If you at one point or another get an error about not having the proper permissions, make sure you put "*sudo*" in front of the command.  If you get more errors, try putting *linux32* in after *sudo*.

For my Doom 3 installation, I don't remember being able to do anything unless I had the '*sudo linux32*' in front of the script that I was trying to execute.  

A note before you attempt any of this , is to copy and past into word editor all the commands you put in + any errors you might have gotten.  This way you can comeback and help future AMD64 users install the original version of NWN.  Its a good habit, because later on you might need to re-install NWN on an AMD64 distro, and bam, you already have all the instructions.

Good Luck!

---

### Post by MelancholyStoo on 2007-05-19
Hey, thanks for the advice.  I had tried using the linux binaries from the Bioware site, but sadly they just refused to run, perhaps it was the lack of lib files but it doesn't really matter now cuz I got it working another way :D

I went to [http://liflg.org/](http://liflg.org/) and downloaded the installers nwn_1.29-multilanguage-2.run and nwn_1.68-english.update.run.  Then I set the permissions to "allow execute" and just ran the first one.  Its a graphical installer that asks for the CDs to be inserted in order.  Then I ran the update and that was that.  The only slight problem was the sound, but after looking at a few other posts on this forum i edited out "./lib" from the library directory path in the nwn file and its fine.

Thanks again for taking the time to help me, I'm going to download the lib files you suggested anyway as I may need them for any future games I try to install.

Stoo.

---

### Post by MelancholyStoo on 2007-05-19
oh, i forgot to mention, I have to turn the compiz cube off or i get a bit of slowdown.  its no worse than when i had it installed on a windows machine a while back, but why put up with it when i don't need to huh?

---

### Post by LuisGMarine on 2007-05-19
I was always told to run things that are graphic demanding without beryl and compiz.  When I ran my regular games I always disabled compiz or beryl, because if I didn't then my games would run supper slow.

Anyhow I'm sorry I didn't point that guide out!  I wanted to, but I completely forgot about it since I didn't think it was going to work for me!  I completely forgot that it was for original!

Anyhow good luck on getting NWN working on your AMD64 box, and hope that it runs smooth , and not run into any problems!

---

### Post by djuhl30 on 2007-05-25
david2@fullMetalA:~/games/nwn$ ldd nwmain
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib32/libm.so.6 (0xf7f27000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f10000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e7a000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7dfa000)
        libmss.so.6 => ./miles/libmss.so.6 (0xf7d86000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7cf7000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bb6000)
        /lib/ld-linux.so.2 (0xf7f69000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf721d000)
        libnvidia-tls.so.1 => /usr/lib32/libnvidia-tls.so.1 (0xf721b000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf720d000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf711c000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7118000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf702e000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7021000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf6f5c000)
        libdirectfb-0.9.so.25 => /usr/lib32/libdirectfb-0.9.so.25 (0xf6f05000)
        libfusion-0.9.so.25 => /usr/lib32/libfusion-0.9.so.25 (0xf6eff000)
        libdirect-0.9.so.25 => /usr/lib32/libdirect-0.9.so.25 (0xf6ef0000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6eec000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6ee7000)

SO I assume it is using the 32 bit libs
but....

david2@fullMetalA:~/games/nwn$ ./nwn
Segmentation fault (core dumped)

What gives?

Dave

---

### Post by MelancholyStoo on 2007-06-01
Not entirely sure, as you said it's using the 32 libs.....
Try searching for "ia32" in synaptic and download any libs that you don't already have.  I had to uninstall/reinstall NWN after faffing around rather unsuccessfully (don't ask).  But on reinstalling it just refused to start, adding the ia32-libs seemed to do the trick.

Let me know how you get on.

Stoo

---

### Post by fakie_flip on 2007-06-04
> **djuhl30 said:**
> david2@fullMetalA:~/games/nwn$ ldd nwmain
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib32/libm.so.6 (0xf7f27000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f10000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e7a000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7dfa000)
        libmss.so.6 => ./miles/libmss.so.6 (0xf7d86000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7cf7000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bb6000)
        /lib/ld-linux.so.2 (0xf7f69000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf721d000)
        libnvidia-tls.so.1 => /usr/lib32/libnvidia-tls.so.1 (0xf721b000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf720d000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf711c000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7118000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf702e000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7021000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf6f5c000)
        libdirectfb-0.9.so.25 => /usr/lib32/libdirectfb-0.9.so.25 (0xf6f05000)
        libfusion-0.9.so.25 => /usr/lib32/libfusion-0.9.so.25 (0xf6eff000)
        libdirect-0.9.so.25 => /usr/lib32/libdirect-0.9.so.25 (0xf6ef0000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6eec000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6ee7000)

SO I assume it is using the 32 bit libs
but....

david2@fullMetalA:~/games/nwn$ ./nwn
Segmentation fault (core dumped)

What gives?

Dave

I had a similar problem. Did you ever figure out the solution?
[http://ubuntuforums.org/showthread.php?p=2777739#post2777739](http://ubuntuforums.org/showthread.php?p=2777739#post2777739)

---

### Post by gtmaneki on 2008-07-31
I had the same problem, but now I think I got something working, although I'm using AMD64 Hardy.  

Here's what I did:

1. Downloaded the loki installers and updates at [http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)

2. Downloaded linux32 from [ftp://ftp.x86-64.org/pub/linux/tools/linux32/](ftp://ftp.x86-64.org/pub/linux/tools/linux32/) and compiled it.

3. Used linux 32 with loki installers/updates to install NWN.  This installed everything to the default directory **/home/[my account]/nwn/**

4. Used installed the ia32-libs package.

5. I opened the file **/home/[my account]/nwn/nwn** and found the line
```

# Library directory
LIBDIR="./lib:./miles"

```

which I changed to 

```

# Library directory
LIBDIR="/usr/lib32:./miles"

```

and saved.  Now when I run nwn, it works.

Good luck!

---

