---
title: "How do I open Heroes Of Newerth?"
date: 2011-05-16
forum: Gaming &amp; Leisure
---

### Post by Onoku on 2011-05-16
So I installed HoN, but I can't figure out how to actually start the game up. I tried hon.sh and the screen flicked black like it was going to do something, then it went away. I do have the file checked to allow it to open as an executable file. Help please?

---

### Post by Perfect Storm on 2011-05-16
Try launch it via the terminal (hon.sh).

---

### Post by HolgerB on 2011-05-16
Hm, you should try to launch hon.sh inside a terminal and watch out for errors.
Sounds like HoN is missing some libs or stuff like that. For me it worked fine (on U10.04) but it is ages ago I tested the beta.

HTH,
Holger

---

### Post by Onoku on 2011-05-16
what is the command in the terminal to launch it? i typed just hon.sh and it didn't work.

---

### Post by Perfect Storm on 2011-05-16
```
cd <path>
sh hon.sh
```

---

### Post by Onoku on 2011-05-16
Thanks AI.

Just tried sh hon.sh and it said "sh: can't open hon.sh" hmm... sometimes I wish things could just work.

---

### Post by HolgerB on 2011-05-16
Oh, sorry, I forgot to mention that you have to open an xterminal.

Try ./hon.sh ;)

---

### Post by Onoku on 2011-05-16
pardon my ignorance, but what is the difference between terminal and xterminal, and where might I find xterminal?

I guess I should specify that I am a new linux user, so some basic stuff might be lost on me.

---

### Post by HolgerB on 2011-05-16
> **Onoku said:**
> pardon my ignorance, but what is the difference between terminal and xterminal, and where might I find xterminal?

I guess I should specify that I am a new linux user, so some basic stuff might be lost on me.
Pardon my ignorance for assuming you know the difference between an xterminal (simply a x-windows based terminal program) and the "normal" terminal you can call by clicking at the Ubuntu menu entry. Based on the windows manager you use (XFCE, KDE, GNOME) the terminal comes in some flavor.

Simply use a terminal program of your choice, move to your HoN directory and try ./hon.sh

---

### Post by ShadowMage on 2011-05-17
Using a regular terminal works for me. Onoku, at any given time the terminal is in some directory (when you open it it should be in your home folder). I'm pretty sure the "sh: can't open hon.sh" error you got was because it couldn't find  hon.sh, because the terminal wasn't in the same directory as hon.sh. You can change directory using the cd command.

So, you should try running the hon.sh file from the terminal, from inside the HoN directory, as AI suggested. From your screenshot, I see that your HoN folder is ~/HoN (~ means your home folder). So, in your case, what you wanna do is try running

```
cd ~/HoN
sh hon.sh
```

---

### Post by -gabe-noob- on 2011-05-31
for me you have to cd to HoN so taht you have the terminal at the /hon line or however I should word that.

Then use ./hon-x86_64 or ./hon-x86 depending on weather you're on 64 bits on 32 bits

---

### Post by -gabe-noob- on 2011-05-31
Note, mark as executable.

---

