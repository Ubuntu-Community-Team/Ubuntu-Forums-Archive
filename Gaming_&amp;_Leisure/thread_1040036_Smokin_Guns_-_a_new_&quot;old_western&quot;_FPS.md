---
title: "Smokin Guns - a new &quot;old western&quot; FPS"
date: 2009-01-15
forum: Gaming &amp; Leisure
---

### Post by electrogeist on 2009-01-15
So I wanted to give Smokin Guns a try.  It was just released as a stand alone game, after starting life as a Quake3 mod called Western Quake.  Smokin Guns is set in the Wild West and offers unique gametypes such as Bank Robbery.

Installation was supposed to be fairly straightforward:  

1) Download for FREE from [http://www.smokin-guns.net/](http://www.smokin-guns.net/)  Get the .zip archive not the .exe. The .zip contains both the ms windows .exe and the linux binary. (340MB)

2) Unzip it.  You can double click the .zip and drag the "Smokin' Guns" directory to your home directory.

3) Rename the directory you just unzipped from "Smokin' Guns" to "SmokinGuns" as the engine will always look for that directory as installed game path.

4) Set execute permission for "smokinguns.x86".  You can right click on the file in Nautilus, select Properties, go to Permissions tab, check box for "Allow executing file as program".  Alternatively "chmod +x smokinguns.x86" on the command line does the same thing.


It was supposed be as simple as that to be able to run ~/SmokinGuns/smokinguns.x86

And it probably is that simple for some people with a 32-bit distro.  However, on this box I have Ubuntu 8.04 64-bit, and a couple more steps were needed...

```

j@blackcreek:~/SmokinGuns$ ./smokinguns.x86
./smokinguns.x86: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

```

Hmmm... it looks like I have libXxf86dga.so.1 right?

```

j@blackcreek:~/SmokinGuns$ locate libXxf
/usr/lib/libXxf86dga.so.1
/usr/lib/libXxf86dga.so.1.0.0
/usr/lib/libXxf86misc.so.1
/usr/lib/libXxf86misc.so.1.1.0
/usr/lib/libXxf86vm.so.1
/usr/lib/libXxf86vm.so.1.0.0
/usr/lib32/libXxf86vm.so.1
/usr/lib32/libXxf86vm.so.1.0.0

```

Oh, there's not a 32-bit libXxf86dga.so.1 in /usr/lib32/ 

At this point I was afraid I might end up in a 32-bit dependancy hell.  Ah, a good time to try out Cappy's getlibs script!
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

```

j@blackcreek:~/SmokinGuns$ getlibs smokinguns.x86 
libXxf86dga.so.1: libxxf86dga1
The following i386 packages will be installed:
libxxf86dga1
Continue [Y/n]? y
Downloading ...
Installing libraries ...
[sudo] password

```

Ok so there was only the one dependancy... Lets try to run the game again!

```

j@blackcreek:~/SmokinGuns$ ./smokinguns.x86 
<<<< snip >>>>
...loading opengl32: QGL_Init: Can't load opengl32 from /etc/ld.so.conf: opengl32: cannot open shared object file: No such file or directory
failed
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf: libGL.so: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

Apparantly everything is there except for a needed symlink.  Smokin Guns is looking for libGL.so not libGL.so.1  I created a symlink for the 64-bit one in /usr/lib too, but just the first line would probably suffice.

```

$ sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
$ sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so

```

Finally it works!

```

j@blackcreek:~/SmokinGuns$ ./smokinguns.x86 

```

Too bad there's only bots at 3:00am... I'm hoping there's human players during normal hours.  (hopefully more players than World of Padman, which is a *really* cool game, but every time I've tried WOP there are never any human players. And I've tried WOP periodically for like 4 years now *sigh*)

---

### Post by nawitus on 2009-01-16
I had a problem with libopenal.so.0,I only got libopenal.so.1.I simply copied the file and it works sofar (not sure if this is the correct way though). getlibs didn't work so I just did this:
```

sudo cp /usr/lib/libopenal.so.1 /usr/lib/libopenal.sp.0

```

---

### Post by alienseer23 on 2009-01-18
Is there a better way to go about this?

---

### Post by electrogeist on 2009-01-18
> **nawitus said:**
> I had a problem with libopenal.so.0,I only got libopenal.so.1.I simply copied the file and it works sofar (not sure if this is the correct way though). getlibs didn't work so I just did this:
```

sudo cp /usr/lib/libopenal.so.1 /usr/lib/libopenal.sp.0

```

Better to create a symbolic link, so that libopenal.so.0 points to libopenal.so.1, and you won't be using an old libopenal.so.0 when libopenal.so.1 gets updated:

```

sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

```

---

### Post by ales on 2009-01-22
Hello,

here is complete guide how to do it. Worked for me fine on 8.10.

[http://nousessence.com/node/1257](http://nousessence.com/node/1257)


Bye.

Ales

---

### Post by NewJack on 2009-01-22
I love westerns.  I'll give this a go later on tonight.

Thanks for the heads up!

---

### Post by 70plymouth on 2009-01-22
I just got it to work but no one is online :(

---

### Post by NewJack on 2009-01-22
> **ales said:**
> Hello,

here is complete guide how to do it. Worked for me fine on 8.10.

[http://nousessence.com/node/1257](http://nousessence.com/node/1257)


Bye.

Ales

Thanks for the link Ales.  Worked like a charm for me on Intrepid.  Cool game.  Hopefully word of mouth gets more people playing.  I'd love to see full servers going.

:D

---

### Post by rv65 on 2009-01-23
```
./smokinguns.x86: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```

No matter how many times it will still do this. Using Intrepid amd64 with OSS 4.1-1051.

---

### Post by Melcar on 2009-01-24
Worked perfectly for me without the need of any of this.  Simply extracted the .zip, made the smokinguns.x86 executable, and ran it.  Hardy 64bit.  Of course, I have several 32bit games running already so maybe I had the fixed dependencies and did not notice it.  I did have to edit the .cfg file to turn off openal though, so as to fix annoying popping from my speakers (happens to me on almost all Quake based games).

---

### Post by Melcar on 2009-01-24
This doesn't seem to be a 64bit issue either.  My laptop running 32bit Kubuntu gives me this same error discussed here.  I'm guessing it's just the missing link that's causing the problems.

Edit:  The way I managed to fix it was simply with:

```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

My system already had libopenal.so.1 and the game looks for libopenal.so.0

---

### Post by ales on 2009-01-25
> **rv65 said:**
> ```
./smokinguns.x86: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```

No matter how many times it will still do this. Using Intrepid amd64 with OSS 4.1-1051.


Just do this:

    * Unzip it in your home folder
    * Rename the base folder from "Smokin' Guns" to "SmokinGuns" as the engine will always look for that folder as installed game path.
    * in a terminal type cd /home/YOUR_USER_NAME/SmokinGuns
    * in a terminal type chmod +x smokinguns.x86
    * create a menu item witch points at /home/YOUR_USER_NAME/SmokinGuns/smokinguns.x86
   [B] * make sure you have th openAL api sudo apt-get install libopenal1
      and make some symlinks sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
      sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0[/B]
    * Play the game!

---

### Post by NewJack on 2009-01-25
Post your ingame name so other Forums people know who you are

<<<<<<< Newjack (Duh :) )

---

### Post by mcpentax on 2009-01-30
> **ales said:**
> Just do this:

    * Unzip it in your home folder
    * Rename the base folder from "Smokin' Guns" to "SmokinGuns" as the engine will always look for that folder as installed game path.
    * in a terminal type cd /home/YOUR_USER_NAME/SmokinGuns
    * in a terminal type chmod +x smokinguns.x86
    * create a menu item witch points at /home/YOUR_USER_NAME/SmokinGuns/smokinguns.x86
   [B] * make sure you have th openAL api sudo apt-get install libopenal1
      and make some symlinks sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
      sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0[/B]
    * Play the game!

I'm on Ubuntu Intrepid x64 and I always get the "error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory" although I followed all the steps in your post without receiving any error until I launch SG.

---

### Post by electrogeist on 2009-01-30
Because for us 64-bit guys, the 32-bit libraries are in the /usr/lib32 directory:

$ sudo ln -s /usr/lib32/libopenal.so.1 /usr/lib32/libopenal.so.0

Hopefully if you ran Cuppy's getlibs script as described in my original post, it would have automatically grabbed the 32-bit libopenal for you if you didn't already have it.  If it didn't, you can do a:

$ getlibs -p libopenal1

---

### Post by mcpentax on 2009-01-31
Thank you electrogeist! that worked...

---

### Post by fchristophersen on 2009-02-04
I'm running xubuntu 8.04, and libopenal package doesn't seem to exist for this version. so i tried running smokinguns.exe with wine... and it works flawlessly!

---

### Post by CowzRule on 2009-02-04
> **NewJack said:**
> Post your ingame name so other Forums people know who you are

<<<<<<< Newjack (Duh :) )

Cool Game :) "CowzRule"

---

### Post by NewJack on 2009-02-04
I hope word of mouth for this game spreads a bit more.  Would be good to have some full servers going.

---

### Post by crazyfuturamanoob on 2009-02-04
This game rocks! Even better than Urban Terror.

Too bad there are very few servers, and even less bot-free servers. (I hate bots)

---

### Post by scheuri on 2009-02-05
Ah, so I am not the only one NOT seeing any servers in the list.
I wondered...

It says (on "refresh list") it finds several hundreds servers, but I do not see any on the list actually...

Maybe I am just very unlucky in times to check for multiplayer-games.

Other than that, the game is funny. however, I would not claim it is better than urban terror...;)

cheers
scheuri

---

### Post by sparcdr on 2009-02-08
I'm one of the team members for the project.

You are free to connect to:
70.38.12.153:27960

By using: ```

connect [server:port]

``` in the console (~)

Else, click get list.  Refresh is only to be used after the full list has been cached.

- James

---

### Post by unplugged23 on 2009-02-09
I LOVE this post. If only there were some way to convince some high up ubuntu executive to add this game to the default repositories so that more people would download it and multi player traffic would be higher. It's games like this that satisfy my switching back to windows. :):):):):):):)

---

### Post by mofrikaantje on 2009-06-02
Sorry for bumping, but the suggested solution to the graphics errors doesn't work with me. I downloaded Smokin Guns in zip, tried to execute and got the standard "OpenGL not found" etc. errors when starting up. I maked a symlink from */etc/libglid-2.0.so* to */etc/libGL.so*, which solved one error. The other one was solved by using *+set r_glDriver "/usr/lib/libGL.so"* as a parameter when starting up (maybe add this solution to the first post as a how-to?). Now however, I get the following output:

```
sander@sander-laptop:~/UrbanTerror/SmokinGuns$ ./smokinguns.x86 +set r_glDriver "/usr/lib/libGL.so"
UID 1000 EUID 1000
SG 1.0 linux-i386 Dec 31 2008
----- FS_Startup -----
pak0 has checksum 2206249363
alamo1 has checksum 3611996451
joekarimat1 has checksum 891991440
sg_maps0 has checksum 3111238755
sg_pak0 has checksum 2450671269
sg_sounds has checksum 1404357192
sg_textures0 has checksum 3110057026
Current search path:
/home/sander/.smokinguns/smokinguns
./smokinguns/sg_textures0.pk3 (1018 files)
./smokinguns/sg_sounds.pk3 (278 files)
./smokinguns/sg_pak0.pk3 (803 files)
./smokinguns/sg_maps0.pk3 (161 files)
./smokinguns/joekarimat1.pk3 (178 files)
./smokinguns/alamo1.pk3 (14 files)
./smokinguns
/home/sander/.q3a/smokinguns
/home/sander/.smokinguns/baseq3
./baseq3/pak0.pk3 (107 files)
./baseq3

----------------------
2559 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading /usr/lib/libGL.so: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
**Received signal 11, exiting...**
```

So, the last line is saying it crashes. I already looked into the matter extensively on the interwebs, but no solution found so far. Setting graphic options in default.cfg to the lowest, didn't help. Other quake-based games such as UrbanTerror and Wolfenstein: Enemy Territory run flawlessly. I have all ATI-drivers installed, no Compiz enabled. (Ubuntu 8.04, for the record)

So... any thoughts?

---

### Post by mofrikaantje on 2009-06-03
Nobody to help me out? :(

---

### Post by mofrikaantje on 2009-06-07
Bump :popcorn:

---

### Post by ales on 2009-06-07
> **mofrikaantje said:**
> Bump :popcorn:

are u using free open source drivers or proprietary?

---

### Post by mofrikaantje on 2009-06-08
> **ales said:**
> are u using free open source drivers or proprietary?

Once more reinstalling my proprietary drivers seemed to solve the problem. Thanks anyway :)

---

### Post by Jestersage on 2009-06-08
I agree. It is one of the best, if not THE best, FPS in terms of gameplay. It's graphic may not be as well as other games, but I find its control to be far better than those for Action Half Life (which have no other copy until now). If one is willing to make it into modern setting and throw in some kung fu stuff, we can have a good Hong Kong Blood opera game.

---

### Post by CharmyBee on 2009-06-08
> **Jestersage said:**
>  I find its control to be far better than those for Action Half Life (which have no other copy until now). If one is willing to make it into modern setting and throw in some kung fu stuff, we can have a good Hong Kong Blood opera game.
I'm surprised no one has taken on this formula in a free game yet. It's proven to be successful years back. Sure, no hostages and bombs to defuse, but the arcade 'movie realism' multiplayer has been lost in recent times for quite a while. No one wants to be a Bronson anymore but a virtual drafted soldier. :(

Action Half-Life 2 fills my gap on this. I've been playing that a lot lately, though the servers tend to crash.

I don't like Smokin' Guns much since the team change by Western Quake3 version 2 or 3. I still have old WQ3 v1.1 installed with Q3 1.17.

---

### Post by mofrikaantje on 2009-06-09
Hah, great. Just upgraded to Jaunty, and the fglrx-drivers keep messing up my x-session. No more quake-games for me.

---

### Post by Cody the Linux Guru on 2009-06-24
I love this game I had to run it in wine though because I couldn't get it to work until I found this thread thanks guys :popcorn:  

my game name is xXsteelcobraXx

---

### Post by iheartubuntu on 2009-07-10
Im downloading this now... looks great. Reminds me of Outlaws, but this looks better. Is there a 3D mode? Wow, that would be awesome.

---

### Post by Noobs*McGee on 2009-07-12
I downloaded and it's working great so far (I just had to apply the fixes that electrogeist recommended).  I'm using Noobs*McGee as my handle ;)

One thing: does anyone know where I could get a good icon for the menu launcher?  Just an aesthetics thing - the springboard is kinda lame...



Edit: nvm, I found the .png file in the SmokinGuns folder ;)

---

### Post by Noobs*McGee on 2009-07-12
Anyone know if it's possible to use Xbox 360 controller as joystick in this game?  I use it with GXMAME, so I know it works with my system...

---

### Post by BbUiDgZ on 2010-11-28
> **Noobs*McGee said:**
> Anyone know if it's possible to use Xbox 360 controller as joystick in this game?  I use it with GXMAME, so I know it works with my system...


thats just wrong

---

