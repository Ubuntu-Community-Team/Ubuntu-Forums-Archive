---
title: "Wolfenstein woes"
date: 2006-06-29
forum: Gaming &amp; Leisure
---

### Post by GuitarHero on 2006-06-29
I just installed Wolfenstein ET.  I cant get sound to work with it.  Also it screws up my resolution.  It creates these black bars on the right and left that give me a square viewing area.  then when i go back to ubuntu i have to reset my resolution to make them go away and get a normal resolution.  Are these common problems that can be fixed with a patch or something or is something really screwed up with my ET.  Its the 2.60 version

---

### Post by jISh on 2006-06-29
These are common problems. I don't know how to fix the graphics one since I personally didn't have it, but you should be able to fix the sound by typing 

killall esd

before playing the game. Can type esd after to enable it again.
Or just put it in the shell script.

---

### Post by GuitarHero on 2006-06-29
How do I put it in the shell script?  Also does that disable and enable it when the program starts/closes?

---

### Post by jISh on 2006-06-29
This is my shell script:

```

cd "/home/mike/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
killall esd
exec ./et.x86 "$@" +set_initsound 1
esd

```

Open your et.sh file with gedit and paste that in, overwrite whatevers in there. If you don't have an et.sh, make one. This will launch the game for you.

Of course, change the /home/mike part to your username and game folder..

And yes, that will disable esd before playing and re-enable it afterwards.

---

### Post by GuitarHero on 2006-06-29
I didnt have one, so i put one in my /usr/local/games/enemy-territory/ folder.  It just made the game open slower.  I dont know if it actually did what its supposed to or not.

---

