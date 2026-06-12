---
title: "doomsday freezes in Gutsy 7.10"
date: 2007-12-26
forum: Gaming &amp; Leisure
---

### Post by dater on 2007-12-26
Hello. I have been trying to get a good Doom port/engine to work for me. I had been playing the freedoom version of doom2 using skulltag, but am constantly getting crashes with it. So, I downloaded the doomsday engine and after allot of trial and error to compile it, finally did. However when I start a new game it freezes after I start moving around or when I click ESC to go to the menu. I use the CTRL-ALT-F1 to log in to command line and kill -9 <PID>. When I go back to X (CTRL-ALT-F7) the screen is at a lower resolution and the mouse no longer works. I CTRL-ALT-DEL to get the logout option using the keyboard. Then when  I log back in, everything is back to normal. Any ideas on what to do to troubleshoot?
I have checked $HOME/.deng/doomsday.out and see no errors. Nothing I can find in DMESG, /var/log/messages, or /var/log/Xorg.0.log.

I have a NVIDIA GeForce 6200 256MB Video Card
ViewSonic VE710b-2 Monitor at 1280X1024 Resolution
AMD Athlon XP 1600+ CPU
1GB RAM

Any help appreciated.
/dater

---

### Post by DoktorSeven on 2007-12-27
The latest versions of doomsday (1.9.0 betas) freeze up on me a lot.  I've always used the 1.8.6 version since they seem infinitely more stable to me.  Note that the old version requires the -maxzone option on the commandline at the end of the other options to allocate memory for it (e.g. **-maxzone 256m** for 256MB.)

As for the resolution/no mouse thing, that's just the result of Doomsday (or any other game similar to it) crashing, it leaves it in a weird state.  If you have a terminal window open, typing **xrandr -s 0** (or CTRL-ALT-Numpad+ or Numpad-) should get the resolution back, but I've never found a way to restore the mouse besides re-running a game similar to that and then exiting it cleanly.

(Compiling it requires the old version of GCC: 
**sudo apt-get install gcc-3.4 g++-3.4** 
and passing that to the configure script: 
**CC="gcc-3.4" CXX="g++-3.4" ./configure** 
all on one line.)

---

### Post by dater on 2007-12-27
Hi DoktorSeven,

Thanks for the update. How would I find the 1.8.6 version? I have searched for it, but I only found the 1.9 beta versions here.
[http://www.doomsdayhq.com/](http://www.doomsdayhq.com/)

TIA!
/dater

---

### Post by dater on 2007-12-27
Let me rephrase. I found the 1.8.6 for Win32, but not for any Linux.
Any ideas where to find the 1.8.6 Linux port?


TIA
/dater

---

### Post by DoktorSeven on 2007-12-27
[http://sourceforge.net/project/showfiles.php?group_id=74815&package_id=75784](http://sourceforge.net/project/showfiles.php?group_id=74815&package_id=75784)

(From [http://sourceforge.net/project/showfiles.php?group_id=74815](http://sourceforge.net/project/showfiles.php?group_id=74815) -> Source code -> View older releases from the Source Code package)

---

### Post by dater on 2007-12-28
Hey DoktorSeven!

Thanks for the link.
I finally got it installed. However when running it, using the following command, the screen is all garbled and I can't make out anything. I know the menu, and can see the red letters, but can't make them out as they are all garbled too, so I hit the up arrow to get the quit, hit ENTER, the "y" to exit. 

Here is my script to start

/usr/local/bin/doomsday -game jdoom -file \ etc/alternatives/doom2.wad \
-userdir ~/doomsday/jdoom -maxzone 256m

I then tried to go up one to 1.9.9beta3, but same thing. In the latest 1.9.0beta5.2 I did not see this, but then it would freeze on me. Any ideas?

TIA,
/dater

---

### Post by DoktorSeven on 2007-12-28
Do you have problems with any other 3d game (that uses OpenGL/direct rendering, like OpenArena for example)?

---

### Post by dater on 2007-12-28
Hi Stephen(found your blog).

No, not exactly. I have seen some stability issues with some such as freezing after playing for a while, but at least the graphics are fine until that time. Haven't tried OpenArena, but have played ArmyOpts, Tremulous, and some others which I believe all use 3d/OpenGL. So, not sure why this is happening here. Any debugging tips would be appreciated.

Also, on another note(sorry if off topic), I have tried your gdoomsday,as far as installing and when I run ./configure it is not finding the GTK 2+ libs. Here is the error.


checking for GTK... configure: error:
                GTK+2.0 or higher must be installed on your system.

                Ensure that the GTK libraries are installed in a standard
                path and that the include headers are installed.  If they
                are installed and cannot be found by the configure 
                script,
                set the GTK_CFLAGS and GTK_LIBS envionment variables 
                to the appropriate locations.

However, best I can tell Gutsy comes with 2.10 as far as checking /usr/lib --> ls /usr/lib/gtk-2.0/
                   2.10.0  modules

So, in order to configure, what should GTK_CFLAGS and GTK_LIBS be set to?

TIA,
/dater(aka Brett)

---

### Post by dater on 2007-12-28
Stephen,

Update on the graphics garbled issue. I found the problem with that.
I had played with my Nvidia-Settings and under Open GL settings I had  set it to the highest. e.g. High Performance. I set it back to "Performance" and now the screen is no longer garbled. Now I will try it out and see if it is stable. Still interested in your feedback on gdoomsday though.

TIA,
/dater

---

### Post by dater on 2007-12-28
Well, another quick update. It still freezes on me with the 1.8.6 version.
I started a new game, then started moving toward the two baddies,and it hung. Tried ESC to go to menu, and nothing there either. I then used CTRL-ALT-F1 to console and killed the PID and then had to restart X(CTRL-ALT-BACKSPACE) to get the resolution and mouse back. I tried the xrandr -s 0 (or CTRL-ALT-Numpad+ or Numpad-), but it didn't seem to work for me. So, not sure what else to try now. I will try setting back the Nvidia performance settings to see if it makes any difference to the freezing, but not sure. 

TIA,
/dater

---

### Post by DoktorSeven on 2007-12-30
gdoomsday (and any other program you have to compile) requires the -dev package of the needed library.  Search for libgtk dev in repos, I believe it's called **libgtk2.0-dev**.

However, I have no idea how you get so many freezing issues with Doomsday.  I've never had problems with it at all.  Does the output of Doomsday give you any strange/unusual messages?

---

