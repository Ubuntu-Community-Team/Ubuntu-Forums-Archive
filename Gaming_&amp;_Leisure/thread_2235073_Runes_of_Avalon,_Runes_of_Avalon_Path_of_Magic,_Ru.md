---
title: "Runes of Avalon, Runes of Avalon: Path of Magic, Runes of Avalon 2 not starting 12.04"
date: 2014-07-18
forum: Gaming &amp; Leisure
---

### Post by LepricahnsGold on 2014-07-18
I cannot get the Runes of Avalon, Runes of Avalon: Path of Magic or Runes of Avalon 2 demos to run on 12.04. If I double-click on the desktop icon or the Runes_of_Avalon_demo file....nothing. If I go into terminal and run the runes_start (for Runes of Avalon) file, I get the following:

lepricahnsgold@lepricahnsgold-System-Product-Name:~$ cd runes_of_avaon_demo
lepricahnsgold@lepricahnsgold-System-Product-Name:~/runes_of_avaon_demo$ ./runes_start
./Runes_of_Avalon_demo: /home/lepricahnsgold/runes_of_avaon_demo/libc.so.6: version `GLIBC_2.8' not found (required by /usr/lib/i386-linux-gnu/mesa/libGL.so.1)
./Runes_of_Avalon_demo: /home/lepricahnsgold/runes_of_avaon_demo/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib/i386-linux-gnu/libGLU.so.1)
./Runes_of_Avalon_demo: /home/lepricahnsgold/runes_of_avaon_demo/libc.so.6: version `GLIBC_2.7' not found (required by /usr/lib/i386-linux-gnu/libdrm.so.2)
lepricahnsgold@lepricahnsgold-System-Product-Name:~/runes_of_avaon_demo$

I get about the same message for RoA: PoM and RoA 2. Sadly, what was suggested here was no help: [http://ubuntuforums.org/showthread.php?t=1311456&highlight=Runes+Avalon](http://ubuntuforums.org/showthread.php?t=1311456&highlight=Runes+Avalon)
libstdc++5 is installed on my system via GNU Standard C++ Library v3 4.6.3-1ubuntu5: i386 from here: [http://packages.ubuntu.com/search?keywords=libstdc%2B%2B6](http://packages.ubuntu.com/search?keywords=libstdc%2B%2B6)

This was no help either: [http://www.anawiki.com/blog/2010/12/01/linux-games-announcement/](http://www.anawiki.com/blog/2010/12/01/linux-games-announcement/)

This is what is in the runes_start file (on my system):

export LD_LIBRARY_PATH="/home/lepricahnsgold/runes_of_avaon_demo":.
cd "/home/lepricahnsgold/runes_of_avaon_demo"
./Runes_of_Avalon_demo

This is the contents of the folder:

/home/lepricahnsgold/runes_of_avaon_demo/data
/home/lepricahnsgold/runes_of_avaon_demo/gfx
/home/lepricahnsgold/runes_of_avaon_demo/sfx
/home/lepricahnsgold/runes_of_avaon_demo/anawiki-runesofavalon.directory
/home/lepricahnsgold/runes_of_avaon_demo/anawiki-buyrunes.desktop
/home/lepricahnsgold/runes_of_avaon_demo/libc.so.6
/home/lepricahnsgold/runes_of_avaon_demo/libstdc++.so.5
/home/lepricahnsgold/runes_of_avaon_demo/libstdc++.so.5.0.7
/home/lepricahnsgold/runes_of_avaon_demo/libX11.so.6
/home/lepricahnsgold/runes_of_avaon_demo/libX11.so.6.2.0
/home/lepricahnsgold/runes_of_avaon_demo/libXxf86vm.so.1
/home/lepricahnsgold/runes_of_avaon_demo/libXxf86vm.so.1.0.0
/home/lepricahnsgold/runes_of_avaon_demo/Licence.txt
/home/lepricahnsgold/runes_of_avaon_demo/postinstall
/home/lepricahnsgold/runes_of_avaon_demo/postuninstall
/home/lepricahnsgold/runes_of_avaon_demo/README
/home/lepricahnsgold/runes_of_avaon_demo/Runes_of_Avalon_demo
/home/lepricahnsgold/runes_of_avaon_demo/anawiki-runesofavalon.desktop
/home/lepricahnsgold/runes_of_avaon_demo/runes_start
/home/lepricahnsgold/runes_of_avaon_demo/uninstall
/home/lepricahnsgold/runes_of_avaon_demo/anawiki-runesofavalonuninstall.desktop
/home/lepricahnsgold/runes_of_avaon_demo/xdg-desktop-menu
/home/lepricahnsgold/runes_of_avaon_demo/xdg-open

I am very much a noob so any help would be appreciated. I have written to Anawiki Games but gotten no response, as yet. Oddly, The Perfect Tree demo ran fine.

---

### Post by LepricahnsGold on 2014-07-19
Solved!

I found the answer on a Path of Magic thread.
I had to add sudo to this line in runes_start: ./Runes_of_Avalon_demo

Now I need to mark this as solved. How do I do that?

---

