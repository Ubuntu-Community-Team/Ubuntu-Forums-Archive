---
title: "Nethack Font Problem - SOLVED"
date: 2008-11-19
forum: Gaming &amp; Leisure
---

### Post by casperlingus on 2008-11-19
I am a huge nethack fan (I even ascended once, many years ago), but I have been struggling to play it on Ubuntu ever since I switched my life over a couple years ago.  ***The fonts/character-sets provided by Ubuntu just don't work.***  Regardless of whether I use a gnome-terminal, and xterm or the console [Ctrl-Alt-F2] it still looks crappy, I even tried installing the original bitmap/VGA font.  

Strictly speaking, the game is playable, but there's no way to get the original nethack feel (unless you want the crappy tiled-graphics versions, which I think damages your ability to quickly process all the information on the screen).  But finally my search is over.  **USE dosbox and the MS-DOS version of nethack**.

**SOLUTION:**
[LIST=1]
[*]Install dosbox  (sudo apt-get install dosbox)
[*]Download MS-DOS version of Nethack [http://www.nethack.org/v343/ports/download-msdos.html]("http://www.nethack.org/v343/ports/download-msdos.html")
[*]Download the recommended CWSDPMI.EXE
[*]Unpack everything into a directory, like /home/casper/nethack
[*]Start dosbox and type
```
mount c: /home/matt/nethack
c:
nethack
```
[*]Hit <alt>-<enter> to enter full-screen mode
[/LIST]

This now looks 100% like the original nethack, which is the ONLY way I can play it.  Maybe, if you haven't been playing nethack for years, you are satisfied with the alternatives, but for me those are intolerable.  It's not about being a snob, it's about being able to process the information on the screen quickly and efficiently, and I learned to do that with this original font set.

I hope someone else benefits from this knowledge, as I have spent much time over the past couple years searching for such a solution.  And this solution is 100%.

-Casper


P.S. - If you would like to have dosbox automatically mount/load, you can do the following:
[LIST=1]
[*]Start dosbox
[*]Mount c: as above
[*]Go to the mounted drive
[*]Type "config -writeconf dosboxrc" into the DOS window
[*]Open a filebrowser or terminal and edit the dosboxrc file
[*]Go to the end of the file, you will see a section labeled "autoexec" and "Lines in this section will be run at startup"
[*]Add the mount command, and c: to this section (below it).  You can even add the nethack command too, if you don't anticipate ever using dosbox for anything else.

[/LIST]

---

