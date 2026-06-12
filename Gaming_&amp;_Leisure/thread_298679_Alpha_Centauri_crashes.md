---
title: "Alpha Centauri crashes?"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by kingrayray on 2006-11-13
When I installed SMAC, I figured I'd run into the typical glibc problems, but i patched it and it launched just fine. The interesting problem comes when I actually start a game, It loads the in-game interface and shows the ship landing (crashing?). At which point it asks me to name my first colony. As soon as I do so, the game crashes giving me the following error:

```
X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #533
  Current Serial #536
```

I don't even know where to begin figuring this out. I thought I was so close! If anybody has this game, and has any advice I'd love some help. Thanks!

---

### Post by Antonlacon on 2006-11-13
Turn off X's composite.

---

### Post by kingrayray on 2006-11-13
Turning off composite didn't make any difference. :/

---

### Post by fycloops on 2006-11-28
I have the same issue.

X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #740
  Current Serial #743

Running:
Edgy (fully updated) 32bit on an amd64 chip.

Would love to be able to play this game. I can't seem to run the patch either.

Fycloops

---

### Post by Leszek Tarkowski on 2006-12-15
I have the same problem. It looks like not related to graphics - game starts, i can see land and landing vehicle and then crashes. I run it in window mode. But of course the same in fullscreen happens. It was working in DD

---

### Post by zergberg on 2007-01-01
Another person with this problem...

Damn Edgy broke everything.

---

### Post by Scotty562 on 2007-02-21
Anyone ever figure this out? I can land and move my unit around but as soon as I try to go into my base mine goes belly-up.

---

### Post by TheIdiotThatIsMe on 2007-03-04
I have the exact same problem, and am in desperate want of help. Really love this game!

---

### Post by fyd on 2007-03-08
Okay, I have run a few tests to investigate this problem:

Kubuntu Dapper: not tested, but it seems some of you guys have and it works.
Kubuntu Edgy (Xorg 7.1): does NOT work, dies before entering the strategic map screen after starting a new game
Kubuntu Feisty Herd 5 liveCD (Xorg 7.2): does NOT work, see above
Fedora Core 7 Test 2 liveCD (Xorg 7.2): does NOT work, dies inside the strategic map screen in the very moment the colony pod is supposed to land on the planet
Gentoo (Xorg 7.0): does work.

And now the interesting bit:

Sabayon Linux liveDVD, based on Gentoo, Xorg 7.2 RC 3: does work! Strange. It seems that this is not a problem related to the upgrade from X 7.0 to 7.1. It does not seem to be an Ubuntu specific problem either because Fedora doesn't work either. Maybe you can contribute other interesting findings so we can solve the problem together?

edit: Seems like I have solved the problem: Just use the same fix as you could for the glibc problem. I'm not sure whether you need the glibc patch (I personally have installed it), but then use the old libraries offered here: [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games) .

---

### Post by Pugwash on 2007-03-10
This worked for me, found  the instructions on a torrent site, the installation instructions which came with the game didn't work ( i got the error listed here - [http://ubuntuforums.org/showthread.php?t=376251&highlight=alpha+centauri](http://ubuntuforums.org/showthread.php?t=376251&highlight=alpha+centauri)). Create an iso of the cd first before proceeding:

> Installation instructions 
1. Open a terminal window 
2. Enter the command 'xhost +localhost' if you don't use Xauthority (if unsure, just do it) 
3. Enter the command 'sudo -s', or 'su' if you don't use sudo (if unsure, try both in the given order) 
4. If you use Xauthority and su, copy the .Xauthority file from your home directory (if unsure and you didn't gain root with sudo, just try it), like so: 

root@linux:/home/voidz0r# cp .Xauthority ~/ 

5. Change the current directory to the download directory, like so: 

root@linux:/home/voidz0r# cd smac 

Replace 'smac' with the actual path. 

6. Enter the command 'mount -o loop Sid_Meiers_Alpha_Centauri-Linux-x86.iso /mnt' 

7. Enter the command 'pushd /mnt' 
8. Enter the command 'bash setup.sh' 
9. Select all installation options 
10. Press 'Begin Install' and wait a while 
11. Press 'Exit' 
12. Enter the command 'popd' 

I couldn't do the next bit, but the game seems to work fine.

>  [I]
13. Enter the command 'bash smac-6.0b-x86.run' 
14. Press 'n', enter 
15. Press enter 
16. Enter the installation path or press enter to accept the default 
17. Enter the command 'exit' [/I]

You should now be able to run the game any time with the command "smacpack".


Edit - You have to run "smackpack" as root or else it doesn't work. Dunno why.

---

### Post by Grey on 2007-03-11
in the alpha centauri root directory, there should be a few shell scripts (at least there are on my box.  I obtained the game through questionable sources, as I already had the Windows version, and couldn't find the linux version for sale anywhere anyway).  Anyways, there should be "smac.dynamic", "smac", "smacx.dynamic" and "smacx".  Just run smac for the statically linked version of the game, or smacx for the expansion.  It works great on Feisty for me.  I played 3 complete games over the weekend.

---

### Post by zergberg on 2007-05-01
> **Pugwash said:**
> 
. . .You have to run "smackpack" as root or else it doesn't work. Dunno why.
I don't really know why this works, but it does. And it's SO AWESOME.

---

### Post by Ash1984 on 2007-05-20
Sorry I to dig up an old thread but I can't get this to work. I have followed the instructions posted and I still get the error message:

X Error: BadMatch
Request Major code 66 ()
Error Serial #740
Current Serial #743

I'm running Ubuntu 7.04 and have installed the planetary pack using Pugwash's instructions. Though I installed the game originally without these instructions but uninstalled it using the uninstall package (seemed to clear it up fine). Would I need to follow the instructions at "how to run old loki games"? The instructions at the weblink seem very unclear.

---

### Post by Ash1984 on 2007-05-20
I have downloaded the old glibc package and extract it to my home folder. I run the command in terminal:

 LD_LIBRARY_PATH=/home/ash/Loki_Compat/ /home/ash/Loki_Compat/ld-linux.so.2 /usr/local/games/smac/smac.dynamic

and get the response:

Creating Loki preferences directory: /home/ash/.loki/
Creating smac preferences directory: /home/ash/.loki/smac
Inconsistency detected by ld.so: dynamic-link.h: 62: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!

---

### Post by uric on 2007-06-21
I get the inconsistency error too, anybody know how to fix that?

---

### Post by BrendanM on 2007-07-01
I'm getting both of these errors. If I try to run the game using just "smac" or "smacpack" I get through the initial menus and then when my ship lands, it crashes out with the:
```

  X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #530
  Current Serial #533
```
(The numbers in the last two lines change). Running as root does not change anything.
If I run with the LD_LIBRARY_PATH... command, I get:
```

Creating smac preferences directory: /home/username/.loki/smac
Inconsistency detected by ld.so: dynamic-link.h: 62: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!
```

I have been following the instructions on the following sites: [http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml](http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml)
[http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)
[http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)

I am running Xubuntu 7.04

---

### Post by BrendanM on 2007-07-01
Success!!! I finally got it working.
After reading this thread: [http://ubuntuforums.org/showthread.php?t=311521&highlight=Alpha+Centauri](http://ubuntuforums.org/showthread.php?t=311521&highlight=Alpha+Centauri)
I added
```

Section "Extensions"
	Option "Composite" "Disable"
EndSection

``` to my xorg.conf, restarted X and now it magically works just starting with "smac".

To summarize, I installed using the normal Loki installer, patched the install following instructions here: [http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)
and then added the above section to xorg and that made it work. I do have the compatibility libraries installed, but they don't seem to be necessary since I'm not using any special commands to launch the game.

---

### Post by Doctoxic on 2007-07-08
[QUOTE=BrendanM;2944043
To summarize, I installed using the normal Loki installer......[/QUOTE]

how did you do this - i can't install the loki installer as it is greyed out and i get an error :
This installation doesn't support glibc-2.1 on Linux / x86

how many people actually have this game working?  would be very grateful for a detailed blow by blow description of exactly what you did

thanks

Doc

PS - when the post talk about 'installing; libs in a certain directory does this mean you just copy them to the directory? - or do you need to do anything else?

thanks again

---

### Post by fatski on 2007-07-10
I have it working, the static version, when I try to start the dynamic version I get the same inconsistency errors as above. I disabled compositing as detailed above to get the static version to work. The only problem is that I can't see the movies, my monitor flicks to no signal when they come on. I can hear sound though. Anybody any idea how to force the movies to play at a reasonable resolution / refresh rate using the static version?

---

### Post by Stormspireiv on 2007-07-10
> **Doctoxic said:**
> how did you do this - i can't install the loki installer as it is greyed out and i get an error :
This installation doesn't support glibc-2.1 on Linux / x86

how many people actually have this game working?  would be very grateful for a detailed blow by blow description of exactly what you did

thanks

Doc

PS - when the post talk about 'installing; libs in a certain directory does this mean you just copy them to the directory? - or do you need to do anything else?

thanks again

Well, I finally got it working. I posted my step-by-step instructions over in this thread.
[http://ubuntuforums.org/showthread.php?t=345846](http://ubuntuforums.org/showthread.php?t=345846)

---

### Post by dia on 2007-07-24
I have got a torrent smac.iso-file and just started as root "sh setup.sh". After installation procedure I startet as a user and got the discussed X Server error message. Then I added the composite disabling lines in the xorg.conf, according to the hints in this thread. After a reboot **it works fine**. Thanks to the community!

I really love this game, so I am very happy that this game is surviving in Linux. In Windows XP there is no chance to get this game started.

---

### Post by handy on 2007-07-24
I remember really enjoying this game on windows years ago.  It was unstable for me then; I would play for some hours & be very much involved in a game & the game would crash.  I could not find a way to stop it from behaving like that.

I think I'll give it a go on Ubuntu & see...

---

### Post by handy on 2007-07-26
I installed the game & it's expansion, I had to use *sudo* sh setup.sh to be able to install the loki installer & so then I let it carry on & install the rest under sudo.

Type smacpack in the terminal & away it went, everything worked the way it should.  I spent some hours playing a game, I would have been probably 2/3 of the way through & the game crashed to a standstill.  Just the same as it used to do on windows all those years ago.  On completely different hardware. :(

Not a fun way to play this type of game at all.

---

### Post by Stormspireiv on 2007-07-26
Did you make sure to change the file permissions on your .loki directory in your home folder?

---

### Post by handy on 2007-07-26
> **Stormspireiv said:**
> Did you make sure to change the file permissions on your .loki directory in your home folder?

They are set to my user name, not root.

As I said everything works perfectly for hours, then the game freezes, & stays frozen.  The same experience on win98se all those years ago.

---

### Post by handy on 2007-07-27
I'm downloading the patch from:

***_[http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)_***

Apparently one of the things the patch fixes is the game crashing on late model hardware.

Fingers crossed.

---

### Post by handy on 2007-07-27
Still troubles, the patch fails with the following error:

*update.sh: line 56: loki_patch: command not found*

Here is the code that it refers to:

[I]# Verify that the loki_patch version is okay
**if loki_patch --verify patch.dat; then**
    :
else
    exit 1
fi[/I]

Which may indicates that the patch is incompatible with my install.

I'll try editing the script, & see if I can really screw things up! 

The game is unplayable so I have nothing to loose but my time.

---

### Post by handy on 2007-07-27
after editing out the script which stops it, posted above, I can move further through & get stopped at the following line:

[I]# Run the patch program
**loki_patch patch.dat $installed[/I]**

With this error:

*update.sh: line 139: loki_patch: command not found*

I don't believe that the patch.dat file is corrupt, it does not want to update my install, it considers itself unsuitable for whatever reason that I can't quite see?

I'll get around to trying the Alien Crossfire game, though I'd astounded if it isn't crash prone too.

---

### Post by Polygon on 2007-07-27
does this guide help anyone?

[http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)

---

### Post by handy on 2007-07-27
> **Polygon said:**
> does this guide help anyone?

[http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)

I'm sure it does, but not me! :)

---

### Post by Stormspireiv on 2007-07-28
> **handy said:**
> after editing out the script which stops it, posted above, I can move further through & get stopped at the following line:

[I]# Run the patch program
**loki_patch patch.dat $installed[/I]**

With this error:

*update.sh: line 139: loki_patch: command not found*

I don't believe that the patch.dat file is corrupt, it does not want to update my install, it considers itself unsuitable for whatever reason that I can't quite see?

I'll get around to trying the Alien Crossfire game, though I'd astounded if it isn't crash prone too.

I could not get that patch to work. You need to get the 6.0b patch. Either Google smac 6.0b or PM me with your email and I'll send it to you.

---

### Post by handy on 2007-07-30
> **Stormspireiv said:**
> I could not get that patch to work. You need to get the 6.0b patch. Either Google smac 6.0b or PM me with your email and I'll send it to you.

Thanks for your reply Stormspireiv, I will try & track down the patch you recommend, if I fail I'll message you.

Thanks for your help.

---

### Post by lorddresefer on 2009-09-02
This is a problem with WINE it is logged on their sight and it says that as soon as you click on a base or wait about 10 minutes the game will crash.  so hopefully next release of WINE we will see an improvement (dont hold your breath)

---

### Post by Arancaytar on 2009-09-10
I added the required three lines to my Xorg.conf file, and everything worked fine for a while.

However, several days later (I don't think it was the very next reboot, actually, but I don't know), my session would not start correctly anymore: The desktop didn't load; I was stuck in a blank screen on login. By running xfix, I restored the original X conf, which made it work again.

Since then, I've no longer been able to use the Options Composite Disable trick, as it breaks X for me...

---

### Post by rettichschnidi on 2009-09-10
Try Xephyr.

---

### Post by earthman on 2010-01-25
I have the game running fine in Mint 8, but it doesn't run full screen, it's "squeezed" into a 1024 x 768 "window" in the middle of the screen. Anybody know why?

I'm not sure why people say this game doesn't work in Windows, it worked for me in XP, Vista, and now 7, no problems at all. Ever hear of compatibility mode?

---

### Post by Mates87 on 2010-01-29
this HOWTO work fine to me.

Install Loki´s Alpha Centauri Planetary Pack and patch it by Loki upgrade. Upgrade was traying to install smac-6.0b-x86.run but it fails so I dont know if upgrade was successful or not.

To run Loki´s Alpha Centauri on Ubuntu 9.10 Karmic add these lines to /etc/X11/xorg.conf and save it.
(logged as root)
1. open terminal
2. mates@mates-laptop:~$ sudo gedit /etc/X11/xorg.conf
3. add these lines

Section "Extensions"
      Option  "Composite"     "Disable"
EndSection

4. save
These lines will disable Compiz Fusion and other visual effects.

5. Now you must restart Xserver by pressing CTRL+ALT+BACKSPACE. (this function must be enabled in “System”->”Preferences”->”Keyboard”
Select the “Layouts” tab and click on the “Layout Options” button.
Select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.)
works with left ALT and left CTRL

After quit Alpha Centauri delete these lines or set "Enable" in added line in xorg.conf and restart X server to run Compiz again.

This work fine for me. Game run fullscreen.
Sorry for my english, it´s not my born language.

---

### Post by pikmaster on 2010-09-30
> **Stormspireiv said:**
> I could not get that patch to work. You need to get the 6.0b patch. Either Google smac 6.0b or PM me with your email and I'll send it to you.

I think this patch is for 64-bit version, I found this today. That's why it cannot find loki_patch, because it cannot really execute 64-bit binary on 32-bit system. You need to look for 6.0b patch.
I found one here:
[http://filebox.vt.edu/users/bhilburn/Public/smac-6.0b-x86.run](http://filebox.vt.edu/users/bhilburn/Public/smac-6.0b-x86.run)

Mirrored here:
[http://sites.google.com/site/superpikmaster/files/smac-6.0b-x86.run](http://sites.google.com/site/superpikmaster/files/smac-6.0b-x86.run)

---

### Post by rettichschnidi on 2010-09-30
Try this one, it will (should) install and update the game without any trouble:
[http://liflg.org/forum/viewtopic.php?t=949&start=0](http://liflg.org/forum/viewtopic.php?t=949&start=0)

I also created a script which will use xephyr, but I have not yet included it. With this one you'll be able to play the game without to fiddling around with xorg.conf.

If you are interested, please tell me and I'll leave a message in this thread when it is released.

---

### Post by Pikestaff on 2011-06-14
Old thread, but bumping to post this here in case this is helpful to anyone.

**_[SIZE="3"]How I Got Sid Meier's Alpha Centauri Working on Linux[/SIZE]_**

*Note: This is for the Loki games Linux version, not the Windows version/GoG.com version.  The Windows version installs and runs in Wine but there are sound glitches and frequent crashes.*

**1.)** Follow steps 1 through 5 [on this guide]("http://blog.hokietux.net/?p=13").  You may have to run sudo to install.

**2.)** Install Xephyr-- it's in the repositories.

Now we're ready to play:

**3.)** Run this in the terminal to open a Xephyr screen:
```
Xephyr :1 -screen 800x600 -extension Composite
```

Note that you can change the screen resolution, or run fullscreen if you like.

**4.)** Run this in another terminal window to start the game:
```
DISPLAY=:1 smacpack
```

...aaaand that's it.  I did all of the above steps last night and the game runs flawlessly for me on Kubuntu 10.04.

Presumably there is a way to make a script/shortcut that will run the terminal commands in step 3 & 4 for you all in one go, so you don't have to do them every time you want to start the game, but I'm a big newbie to that sort of thing, so someone smarter than I will have to step in and tell us how to do that. :p

---

### Post by handy on 2011-06-14
**@Pikestaff:** Could you give us an update after a month of use?

I've tried everything available on WinXP, OSX & Linux, (on more than one machine) & in the end unreliability rules. To the point that I doubt I'd waste my time with the game again.

---

### Post by Pikestaff on 2011-06-14
> **handy said:**
> **@Pikestaff:** Could you give us an update after a month of use?

I've tried everything available on WinXP, OSX & Linux, (on more than one machine) & in the end unreliability rules. To the point that I doubt I'd waste my time with the game again.

Sure thing.  I've played a couple "test games" already from start to finish without issue, but I will keep you updated.

---

### Post by handy on 2011-06-15
8) I hope you have reliability as it is a great game.

---

### Post by directhex on 2012-10-04
The true workaround is to export XLIB_SKIP_ARGB_VISUALS=1 before running smacpack. No need for Xephyr, no need to disable Composite.

---

### Post by wildmanne39 on 2012-10-06
Thanks for sharing. Thread Closed.

---

