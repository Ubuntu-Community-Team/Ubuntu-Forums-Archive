---
title: "dgen segmentation fault"
date: 2007-02-10
forum: Gaming &amp; Leisure
---

### Post by aanderse on 2007-02-10
hey i installed dgen for 64bit ubuntu and whenever i try to run it it gives me a segmentation fault.  If anyone has any ideas or has fixed this problem i could sure use some help.

thanks

---

### Post by aanderse on 2007-03-08
anyone?

---

### Post by aanderse on 2007-03-29
bump, just incase

---

### Post by Count on 2007-03-31
I have the same problem as aanderse. Also checked to make sure that I had all the dependencies, which I did. I also don't appear to be leaving out any options, but I may be wrong. Google didn't turn up any fixes, but it looks like the segmentation fault is a caused by a problem with sdl.

---

### Post by 1veedo on 2008-09-21
Same problem here got it strait from the package manager.

64bit.

---

### Post by FranMichaels on 2008-09-21
You could try [gens]("http://ubuntuforums.org/showthread.php?t=290008") or [sdlmess]("http://rbelmont.mameworld.info/?page_id=163").

---

### Post by purplemonk on 2008-11-21
> **FranMichaels said:**
> You could try [gens]("http://ubuntuforums.org/showthread.php?t=290008") or [sdlmess]("http://rbelmont.mameworld.info/?page_id=163").

No luck for gens :(

~/src/gens-2.15.5-gs-m5.3$ ./configure --prefix=/usr/local/ && make && make install
[...]
configure: error: 64-bit is currently not supported.

---

### Post by dfreer on 2008-11-21
> **purplemonk said:**
> No luck for gens :(

~/src/gens-2.15.5-gs-m5.3$ ./configure --prefix=/usr/local/ && make && make install
[...]
configure: error: 64-bit is currently not supported.

Try finding a pre-compiled binary, or create a 32-bit chroot and compile in that. Finally, you can also try cross-compiling into a 32-bit binary, that may work as well.

---

### Post by Rounin on 2009-04-07
Meanwhile, if you're really eager, KGEN98 runs just fine via Dosbox. The audio is sometimes glitchy when it starts up, which requires a restart of KGEN98. (It may also help to generate a config file for Dosbox and set it to use a higher sample rate for the audio, such as 44100.) Also, the controller settings seem to be resat each time the program is run, and the menus have to be navigated using the numpad, not the regular arrow keys. Oh, and it's laggy. OK, so maybe not "just fine", but at least it runs.

---

### Post by fdm on 2009-06-26
[ubuntu 9.04 32bit] dgen from the ubuntu repos also gives me segmentation faults. it will usually load a rom for a couple of seconds and then crash. i tried multiple configurations. my work-around was to use gens from sourceforge(.deb package) which works almost flawlessly for me.

---

### Post by Rounin on 2010-01-31
Dear friends; I've found a temporary solution that at leat works on my (64-bit) system. The emulator [Regen](http://aamirm.hacking-cult.org/index_files/regen.htm), which does actually have a Linux version, but seems to require GTK 1, also has a Windows version that will run just fine in Wine.

Fullscreen mode doesn't work properly, and the graphics were buggy at first, but I was able to get flawless graphics in windowed mode by enabling "Superfast rendering", closing the program and then restarting it.

Attempting to remap the controllers seems to crash the program, but the keys are fairly straightforward – A, S, D and Return, I believe.

---

### Post by Rounin on 2010-06-25
After a bit of tinkering, SDLMESS actually turned out to work pretty well – It's just not the pinnacle of user friendliness.

The web site can be found here:

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

And possibly some .debs here:

[http://journalxtra.com/2009/11/how-to-install-sdlmame-and-sdlmess-onto-ubuntu/](http://journalxtra.com/2009/11/how-to-install-sdlmame-and-sdlmess-onto-ubuntu/)

SDLMESS is started like this:

mess genesis -cartridge <romname>

However, there's also a built-in GUI that can be used to select games. In order to activate this GUI, SDLMESS has to be pointed to a valid path from the command-line so that it doesn't give up and quit:

mess genesis -cartridge /home/someuser/games/

Then TAB should be pressed.

Also, to ensure that games run smoothly at all, Ctrl-F8 should be pressed to ensure that frameskipping is set to "auto" or to a high value – Ctrl-F8 and Ctrl-F9 cycle through the modes.

So, there you have it – Just a bit of the good old open-a-fake-ROM-TAB-Ctrl-F8 routine, and SDLMESS runs fine.

---

### Post by Rounin on 2010-11-14
Now I've been able to install Gens/GS by following this advice:

[http://www.backports.ubuntuforums.org/showpost.php?p=4965776&postcount=6](http://www.backports.ubuntuforums.org/showpost.php?p=4965776&postcount=6)

---

### Post by headcount on 2011-02-27
^ Awesome, got this working in 10.10 64-bit thanks to your post.  Appreciate it!

---

### Post by Rounin on 2012-03-17
While I haven't been able to install Gens in Ubuntu 11.10 because of a missing 32-bit version of SDL, it's working agin in the 12.04 beta.

dpkg still complains of a missing 32-bit version of xdg-utils, but as long as the 64-bit version of xdg-utils is installed, as well as the ia32-libs-multiarch package, the error can be ignored like so:

dpkg --force-depends -i Gens_2.16.7_i386.deb

Ah, expect APT to complain constantly, though, and refuse to work until it's uninstalled again.

---

