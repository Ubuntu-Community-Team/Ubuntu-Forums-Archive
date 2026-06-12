---
title: "Space Empires 4 + Wine"
date: 2005-12-01
forum: Gaming &amp; Leisure
---

### Post by the_purulent on 2005-12-01
I installed SE4 Gold last night, everything seemed to go along quite smoothly, and the game loads and runs excellently! However, when I end my turn, it crashes with an error saying ("SE4: File Access Denied").

Any suggestions as to what may be causing this?

---

### Post by teaker1s on 2005-12-01
maybe the read write permissions on the file need changing or maybe it's a bug I tried strong dc++ in wine and it complained a folder was missing when it wasn't

---

### Post by AndersAA on 2005-12-01
wild guess, you copied it from a windows partition?  If you did all the files are marked read only.

try chmod u+w -R directory

(user + write and recursive)

---

### Post by the_purulent on 2005-12-01
I didn't copy from a windows install, but I will try changing the permissions on the install directory for the game.

Funny I didn't even think of that :) Thanks I'll let you know!

---

### Post by the_purulent on 2005-12-01
hmmm that doesn't seem to have helped... still get the wierd non-descript error message.

---

### Post by the_purulent on 2005-12-02
bump

---

### Post by YokoZar on 2005-12-03
Where did you install it to?  Your virtual windows drive should be in ~/.wine/drive_c/, and it should be read/writable by your user.

---

### Post by the_purulent on 2005-12-05
I got it working.
I just used a chmod 777 -R and that did the trick.

---

### Post by Perfect Storm on 2005-12-05
How's the font? Last time I tried it there was no font at all, but it was a year back. Perhaps I should give it a try again and perhaps find the font its missing if the case is the same.

---

### Post by the_purulent on 2005-12-05
The fonts all work with no problems.  Only issue I have is the white text over the dark blue background they use in the text boxes hurts the eyes.  :)

But that has nothing to do with wine, just old aesthetics and graphic design. On a flat panel monitor.

---

### Post by the_purulent on 2005-12-05
Hmm turns out if you upgrade to the Delux Version it causes another issue.
I upgraded from Gold to Delux v1.94 anf got:

External Exception 80000100

As I started the game, it occurs occasionally as I run the game as well. Curious

My problem stems from the builtin quartz.dll.  Does anyone know how I can set a library override to the native quartz.dll file I've downloaded?  When I try to do it in the wincfg utility all the add override buttons are greyed out.

---

