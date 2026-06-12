---
title: "America's Army on 16 bit ;/"
date: 2008-11-22
forum: Gaming &amp; Leisure
---

### Post by l!nux user on 2008-11-22
hello!
i have i problem i downloaded America's Army 2.5.0
installed it by using xterm, i typed there this:
chmod +x armyops250linux2.run 
than:
./armyops250linux2.run.....................all good installed and unpacked
now i try to run it first it's loading but than crashes...
i know the reason, but i don't know how to fix it?
reason is i'm using 16 bit in my xorg configures...game needs 24
i puted 24 and tryed to start it again....finally it started but now it lags....
so plz does anybody has any ideas how to run AA on 16 bit 

thx very much

l!nux

---

### Post by Vadi on 2008-11-22
What is your video card?

---

### Post by l!nux user on 2008-11-22
> **Vadi said:**
> What is your video card?
 
must check because i'm not sure

---

### Post by eragon100 on 2008-11-22
Type lspci in a terminal and post the output here, please.

I will go to sleep now, but I will look here again in the morning :wink:

By the way, do you have desktop effects enabled? They **very** often cause this kind of problems, but they are on by default. (no, I don't understand why :))
Go to System -> Preferences -> Appearance, and then to the tab "Visual Effects". If it's not set to that already, set it to "None" and click the Close button in the
lower right corner of the window. Now try to run the game again, and it should work better.

If the desktop effects are already of, or if the game still lags after they are disabled, you might have to install drivers for your video card (don't worry, this is extremely simple in ubuntu), or it might be that your graphics card simply isn't fast enough to run the game smoothly. That's why I'd like you to run the command posted above, if disabling desktop effects doesn't help.

---

