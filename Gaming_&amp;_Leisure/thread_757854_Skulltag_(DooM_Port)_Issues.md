---
title: "Skulltag (DooM Port) Issues"
date: 2008-04-17
forum: Gaming &amp; Leisure
---

### Post by AoDZelda on 2008-04-17
I'm running Gibbon, soon to upgrade to Heron. I'm having issues running Skulltag. I've followed other peoples posts how to install and run it without success. 

Install fmod3, download the deb, unpack/extract, place iwad in directory and run. 

Did just that. I can't get it to work. I've also tried to run from terminal by navigating to directory and then in terminal typing skulltag. How am I to run this? 

Any more info needed? Any help is appreciated! Thanks

---

### Post by disturbedite on 2008-04-17
it should work.  either you're not doing something correctly or there is actually a problem.

what is the path to the skulltag binary?  type this in a term:
```
/path/to/skulltag/skulltag
```

i have skulltag installed in /usr/share/games/skulltag

so if i wanted to launch it from command line i would type:
```
/usr/share/games/skulltag/skulltag
```

btw, the new version (0.97d) was released.  you should update to it if you haven't already.

---

### Post by AoDZelda on 2008-04-17
well I have extracted the program to ~/Documents/Skulltag

Would it be a better idea to put it in ~/usr/share/games/skulltag ?

I have downloaded the 097d version. I downloaded it 2 days ago, and been trying to make it work since.

---

### Post by disturbedite on 2008-04-17
not really, it doesn't matter where you put it.  i just put it there cuz that is prolly where it would install if it was packaged into a deb package.  (like other programs).

did you try exactly what i said?

---

### Post by AoDZelda on 2008-04-17
Yes. I have put them there also in attempt to fix it. Yesterday before I posted. Still have no luck. How am I to run this? From terminal or from the Applications menu? Id have to add it.

---

### Post by AoDZelda on 2008-04-17
> **disturbedite said:**
> it should work.  either you're not doing something correctly or there is actually a problem.

what is the path to the skulltag binary?  type this in a term:
```
/path/to/skulltag/skulltag
```

i have skulltag installed in /usr/share/games/skulltag

so if i wanted to launch it from command line i would type:
```
/usr/share/games/skulltag/skulltag
```

btw, the new version (0.97d) was released.  you should update to it if you haven't already.

zelda@zelda-desktop:~$ /path/to/skulltag/skulltag+
bash: /path/to/skulltag/skulltag+: No such file or directory

There isnt a .deb of it either.

---

### Post by disturbedite on 2008-04-18
uuuuuuuugggggggggghhhhhhh.......
sorry, i didn't realize you were a noob.  i should have noticed that based on your post count.

/path/to/skulltag means where you installed it.

and i know there isn't a deb package of it, i didn't say there was.

as i asked before, and you didn't answer, where did you install/extract the contents of the packages?

---

### Post by AoDZelda on 2008-04-20
I stated that I installed it in ~/usr/share/games/skulltag.

Yeah. I am a noob. Whats it to you? Im trying to get away from Microsoft. You should be proud.

---

### Post by disturbedite on 2008-04-21
ok.
then execute it this way:
```
/usr/share/games/skulltag/skulltag
```
NOT
~/
that is something different.
now post the output.

i just have to explain things more with a noob, that is all.

---

