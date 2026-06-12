---
title: "Fglrx and AIGLX"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by GameKing505 on 2007-12-17
Well I had Compiz working for a while, but decided to ditch it because I didn't like XGL. It was too buggy and sometimes made weird pixels on my panels and whatnot. I looked into ways of having Compiz working without XGL, and I saw AIGLX.

My video card is a Radeon Xpress 1100, and in the release notes I saw that the latest version of fglrx has AIGLX support for my card. I try to run compiz, and I get "the composite extension is not available." 

I believe that the source of the problem is that I didn't update fglrx for a while. I ran the updater, but it says everything is up to date. Is there any way to tell what version of fglrx I am using, and if it is an old version, to update it?

PS. My updater hasn't told me to update anything for a really long time. I don't know if it's just not working or doing it behing the scenes. I can't be positive about this however.

---

### Post by Espreon on 2007-12-17
Its not worth it. fglrx does not work well with AIGLX as of now. It would be hella slow. The fglrx devs stated that.

---

### Post by GameKing505 on 2007-12-17
I would like to at least try it. I also want to know if my update system is broke, so it anyone out there has any tips, I'd be much obliged.

---

### Post by GameKing505 on 2007-12-18
Pretty please with sugar on top?

---

### Post by erfahren on 2007-12-18
```

fglrxinfo

```

---

### Post by erfahren on 2007-12-18
maybe I should explain this (the best I can)

Unlike Windows, drivers are compiled into the kernel in Linux. So to update a driver it needs to be released with an upgrade of the kernel or re-compiled into the kernel manually. It's not all that difficult(?) but the Ubuntu developers (most likely) wait until a good, stable version of a proprietary driver is released by the vendor before upgrading the kernel with it.

The last real stable version was released with Gutsy. 

You can go through the steps of updating to the newest version from ATI if you want. Whether or not it works great or not is another thing. there is a guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

(note: we have the same card. I tried that ATI 7.11 driver - with the AIGLX support - but I had problems ( [mentioned on this thread](http://ubuntuforums.org/showthread.php?p=3824483) ).
another thread about it: [http://ubuntuforums.org/showthread.php?t=619714](http://ubuntuforums.org/showthread.php?t=619714) --- Edit: actually that's the same thread - lol - oops!

I reverted back to Feisty mainly because of the suspend problems I had with Gutsy, but XGL actually runs a little better on Feisty I think.

BTW: just curious -- what driver version did the output of fglrxinfo give you? With Feisty mine is 8.34.8

---

### Post by GameKing505 on 2007-12-19
Thank you very much for your reply. You were very helpful. So if I understand correctly, when I click the restricted drivers manager and download fglrx, it does not simply install packages but actually compiles itself into the kernel? 

I guess I will wait for fglrx to become more stable with compiz, and for ubuntu to update the restricted drivers manager with the new driver.

btw, fglrxinfo gave me:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
```

---

### Post by Takster on 2007-12-19
I've had very few problems myself so far, seems to run fine for me, compiz does all it's fancy cubes and skydomes and stuff, video plays nicely. Maybe I'm just lucky.

Latest ATI driver.
> 
tak@Marduk:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7059 Release


---

### Post by erfahren on 2007-12-19
> **GameKing505 said:**
> Thank you very much for your reply. You were very helpful. So if I understand correctly, when I click the restricted drivers manager and download fglrx, it does not simply install packages but actually compiles itself into the kernel? ......

LOL - you got me there! 

I think it's more of a situation where the the kernel is already compiled and prepared for it and you just download it if needed. (It also has something to do with the "linux-restricted-modules".)

Actually, after looking back through that guide I linked to, it needs to be compiled into the kernel *module* - so I think that the linux-restricted-modules is already prepared for it.


One note: there is a script/program called [envy](http://albertomilone.com/index.html) that downloads, installs, and configures the latest driver for you. I think it undoes the changes made pretty well if needed.

There's somewhat of a bad history with the ATI proprietary drivers regarding desktop effects and XGL (there's tons of threads about it on the forums).  With Feisty you have to set up a seperate session for XGL. So it's getting better.

---

### Post by erfahren on 2007-12-19
> **Takster said:**
> I've had very few problems myself so far, seems to run fine for me, compiz does all it's fancy cubes and skydomes and stuff, video plays nicely. Maybe I'm just lucky.


maybe my budget notebook is just finicky. I've considered that possibility! lol

---

