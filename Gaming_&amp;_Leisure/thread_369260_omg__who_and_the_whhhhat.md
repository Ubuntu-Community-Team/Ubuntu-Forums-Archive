---
title: "omg  who and the whhhhat ?"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by elaspeinreason on 2007-02-24
i just checked the Ubuntu Gaming website [http://gaming.gwos.org](http://gaming.gwos.org) and there  is NOTHING but an all black screen and what appears to be a repeating image of a diablo character..
also mentioning that it had been  " hacked by iskorpitx "
 after waiting multiple minutes the screen is redirected to an all black page with the address [http://financeaustralia.com.au/tempi/](http://financeaustralia.com.au/tempi/)

whhat  is going on ? joke ?

---

### Post by matthew on 2007-02-24
It got hacked. The site admins are working on it.

---

### Post by Perfect Storm on 2007-02-24
It will be up and running within the next 24 hours.

---

### Post by elaspeinreason on 2007-02-24
thats so  unfortunate  ,  i was had just finished installing mY FIRST ( but not last )  LINUX  game-  Tremulous buttt ive been unable to  play due to : 

You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
[B]
is there anyone here  who  can help with me this situation ????[/B]

---

### Post by Perfect Storm on 2007-02-24
Which card do you have? And which 3D driver do you have installed?

---

### Post by elaspeinreason on 2007-02-24
i  am  unsure as to the card model and 3d driver..
i can tell you i am using a Dell Latitude C-Series PPX PIII 128mbRAM
from the research i have  done thus far it would seem as if i need to activate the hardware  acceleration ...or  install new drivers ?

**  is there a function  i can run  , or a way to check my system specs..as im not  quite sure what i am running
also , if i were to install XFCE would i still be able to play 3daccelerated games ?

---

### Post by elaspeinreason on 2007-02-24
is this  a common problem?  someone please help , i'd hate to be gameless forever on ubuntu.

---

### Post by Perfect Storm on 2007-02-24
```
cat /etc/X11/xorg.conf
```

Please post.

---

### Post by The Noble on 2007-02-24
Yes, you can still run accelerated games in xfce, so no worries. If you could type lspci in the the terminal (it will output quite a bit of info) and something like this should be one of those lines. 
```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

If you do, you will need to set aside about an hour or two to get it working (barely). I have the same card in my other laptop and I was able to get it working after some serious tweaking.  The guide I used should help;

```

http://www.ubuntuforums.org/showthread.php?t=7200&highlight=rage+p%2Fm

```
Note that I got it working, but the performance was extremely lackluster. The card only has 4-8 meg Vram, which is nothing. 4 Meg Vram is required for just displaying the screen in 1024x768 at 24 bit, so toning your bit depth to 16 bit should help a lot. Good luck.

---

