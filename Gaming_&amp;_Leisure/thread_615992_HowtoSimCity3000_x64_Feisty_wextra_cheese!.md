---
title: "Howto:SimCity3000 x64 Feisty w/extra cheese!"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by skoal on 2007-11-17
[FONT="Verdana"]Per your requests, I thought I'd update my Sim City 3000 link for Feisty while I have the time.  I'm chomping on a scrumptious Sonic foot long Coney while I post - extra cheddar and onions and all that sloppy gooey goodness. So, bear with me...

If you don't have it already get util-linux
```
sudo apt-get install util-linux
```
Now, go over to your book shelf where you stash all your old Loki Titles. Grab the Blue Box and carefully scratch off the Brown Recluse spider eggs all over it with your finger nail. Then, insert the CD into that fancy doodad you normally hang your wet socks on to dry. Press the button to close the dryer drawer.

Type in some more console farfegnugen...
```
sudo linux32 sh /media/cdrom/setup.sh
```
I use the Loki defaults and answer Y to everything. However, if you get the strange sensation while following this tutorial that I'm holding your hand at every step, feel free to step out into the 5 foot water without the Pokemon floaties.
```

Would you like to read the /media/cdrom0/README file ? [Y/n] n
Please enter the installation path [/usr/local/games/SC3U]

Hit enter. 
```
```
Please enter the path in which to create the symbolic links [/usr/local/bin]

Hit enter.
```
```
Install Data Files? [Y/n] y
Install Music Files? [N/y] y
Install Intro movie? [N/y] y
Install Landmark Packs? [Y/n/?] y
Install Building Architect Plus? [Y/n] y
Do you want to install desktop items? [Y/n] y
Installing to /usr/local/games/SC3U
40064 MB available, 589 MB will be installed.

Continue install? [Y/n] y
```
Go hit the head real quick or take the time to balance your checkbook. Garbledy gook will fly past your screen super fast for a few minutes. Even if Data tried to read it his head would suffer a melt down like the Wizard of Oz witch thrown into a bucket of water.
```
[...]
 100% - /usr/local/games/SC3U/res/ba/hotkeys/english/000000b1.key
 100% - /usr/local/games/SC3U/README

Installation complete.
```
Well, almost. We need to get this ancient LP45 to spit out some missing tracks.
```
sudo cp -a /media/cdrom/bin/x86/glibc-2.1/* /usr/local/games/SC3U/
```

Y'arr. Patch time, matey! The old bilge rats who once hosted these files have dropped anchor and set sea.

It's mighty slim pickins to find the actual patch these days. In order of Snow White dwarf speed, we have [Loki](http://updates.lokigames.com/sc3u/), [Pokey](http://www.atomicgamer.com/file.php?id=12862), or [Jokey](http://www.fileplanet.com/51959/50000/fileinfo/SimCity-3000-Patch-2.0a-(Linux))!
Take the Loki link. The other two will put you to sleep faster than waiting on Mel Tillis to finish the Alphabet.

Drop the patch in the /tmp folder, and
```
sudo linux32 /bin/bash /tmp/sc3u-2.0a-x86.run
```
```
Would you like to read the README for this update? [Y/n]: n
Would you like to apply this update? [Y/n]: y
Please enter the installation path: []: /usr/local/games/SC3U

Product updated successfully.
```
Oh, really? Lie to me some more, baby.

Create this shell script in an editor. Save it as sc3u in the /usr/local/bin directory.
```
#!/bin/sh
Loki_Compat=/usr/local/games/Loki_Compat
export Loki_Compat

LD_LIBRARY_PATH=$Loki_Compat \
                $Loki_Compat/ld-linux.so.2 \
                /usr/local/games/SC3U/sc3u.dynamic
```
Now, make it executable - like the author should be for writing this goofy howto.
```
chmod u+x /usr/local/bin/sc3u
```
Grab the Loki compatibility libs from the [gentoo](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games) howto [here](http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.2.tar.bz2).

Save the loki_compat_libs-1.2.tar.bz2 file into /tmp, and...
```
sudo tar xvjf /tmp/loki_compat_libs-1.2.tar.bz2 -C /usr/local/games/
```

*The Final Step!*
```
sc3u
```
Pat yourself on the back, partner. Or look into a bathroom mirror and repeat, "Don't you go and die on me!" Wink back to yourself and then strut back to your computer chair to play some Sim City 3000 on your x64 Ubudoobie distro!

[SIZE="6"]What's latin for Caveat Lector?[/SIZE]

By the way, is there a catch? You betcha! If you have ia32-libs installed, you will get this error while using these Loki compat libs...
```
Inconsistency detected by ld.so: dynamic-link.h: 62: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!
```
Just uninstall it.
```
sudo apt-get remove ia32-libs
```
WARNING! DANGER! DANGER WILL ROBINSON! That means no flash and nsplugin wrapper for firefox. Eh, no big whoop. Just reinstall ia32-libs if you get the hunkering for the American Idol amateur hour on youtube.

If, however, you are a glutton for punishment, go grab yourself a bottle of that squishy lemon juice bottle and use that instead for your contact solution cleaner. Then, proceed to chroot and cross compile for the 2.95 kernel and make your own Loki compat libs. I gotta catch a flight tomorrow and don't have the time. So, for now, bye bye amigos, err, ubudoobie brothers and sisters!

\\//_[/FONT]

---

### Post by s1300045 on 2008-02-14
I was looking for a way to install SimCity3000 on my gustyx64 and I tried your method... it works like a charm! I can't believe how easy it is just follow your instruction step by step!

However, there is a rather minor problem. During the process of remove ia32-libs, my wine and nspluginwrapper and fglrx are also removed.....

well, thats just how far I would go to play simcity :lolflag:

---

### Post by stevejesus on 2008-02-25
Well!  This is neat.  I have the Linux copy around somewhere...  but first...  what are the risks of installing Linux32?  What does it do?  I know what the name implies, but I thought I could just use ia32libs...
Anyway, I attempted to install "Linux32", and my shell prompted me, if I remember clearly, to type an entire phrase in order to continue.  
I got scared and backed out.

---

### Post by ceixeoida on 2008-10-19
I tried this in Hardy x64, but...

-When I try to update the game, this is what I get:
```
Creating directory sc3u-2.0a-x86
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 3279358048 2069455402

```

So, the rest of this solution is not suitable for me... suggestions?

---

