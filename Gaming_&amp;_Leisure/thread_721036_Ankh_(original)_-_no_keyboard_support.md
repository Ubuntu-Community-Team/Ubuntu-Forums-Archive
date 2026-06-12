---
title: "Ankh (original) - no keyboard support"
date: 2008-03-10
forum: Gaming &amp; Leisure
---

### Post by ainemoire on 2008-03-10
Hi all-
I'm sorry if this has been answered, but I have looked all over the web and tried so many things I can't even remember what I've done. After looking *again* tonight, and not seeing any help, I thought I'd try this.

My keyboard *does not* work in Ankh (original version). I have installed the patch from Deck13 and the install went fine.

Also, I did check my libSDL version per the Deck13 website, and I have version 11 (they specify version 8 or higher).

I have tried every single key, and nothing. The only thing that does work is Ctrl+Alt+Backspace

Everything else about the game seems to be running great.
I'm running Ubuntu Gutsy on a Celeron D 2.8GHz, 1GB RAM, nVidia GEForce 8400GS 512MB. I've got CompizFusion working fine, and other games like PadMan run just fine (keyboard controls and all).
Help?

TiA  :)

---

### Post by elvinatom on 2009-01-18
I know this is a little late, but I have a solution (just in case someone comes across this):

1. Start a terminal and change to root.
2. Change to install directory.
3. Install Ankh and _DON'T_ start game after install.
4. Apply patches (if any).
5. Change to directory that contains Ankh.
6. Give read/write access to everybody.
7. Close the terminal and enjoy!

Might look like this:
```
su
cd /media/cdrom0
./setup.sh
#### Patches go in here ####
cd /usr/local/games
chmod -R oga+rw Ankh
exit
exit
```

That solved the keyboard problem for me.

---

