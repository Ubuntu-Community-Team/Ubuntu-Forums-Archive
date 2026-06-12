---
title: "dell inspiron 8000 help(moniter)"
date: 2008-02-21
forum: Dell  Ubuntu Support
---

### Post by adamwe1012 on 2008-02-21
K well im really new here, i was just told about ubuntu after my laptop got a REALLY bad virus and i was sick w/ xp either way.  I was told to get the new 7.10 for my laptop but i have this really weird problem, the screen is cut up and it flickers ALOT.  Somesimple fixes would be nice but im really new to this stuff and a few step by steps would be nice, thx for any replies.

---

### Post by pytheas22 on 2008-02-21
I think that Inspirons all come with Intel graphics cards.  If this is true, then trying a different version of the Intel graphics driver might help you.  Do this:

Open a terminal and type:

```
sudo apt-get install xserver-xorg-video-intel
sudo sed 's/i810/intel/' /etc/X11/xorg.conf
```

Report back on the results.  If this doesn't help there are plenty of other things to try.  Also it would be helpful if you posted the contents of your /etc/X11/xorg.conf file, which you could view from the command line using the command

```
cat /etc/X11/xorg.conf
```

or you could navigate to it graphically and open it that way.

---

### Post by adamwe1012 on 2008-02-21
ok well now there is a new problem, i was running off the cd the whole time so i thought installing it would help, but it freezes at %15, and i looked it up and it has a ATI Mobility AGP 4X if thats any help

---

### Post by pytheas22 on 2008-02-21
ok, sorry for the mistake; the intel driver wouldn't make a difference then.  I think that there are two versions of the ATI driver as well, open-source and proprietary, so trying the closed-source version might help, but I've never had an ATI card and don't know.

But before dealing with all that, you should have an installed system.  What does the installer say when it freezes?  Did you check your CD for defects (there's an option for this at the menu when you first boot to the CD)?  Did you try more than once with the same result?

---

### Post by adamwe1012 on 2008-02-21
well, i havent tried for defectes because i just burned it but i will tomarrow, also it freezes at the hard drive part but ill use boot n' nuke tomarrow and hope that helps but for now im going to bed(11:30 here)

---

### Post by pytheas22 on 2008-02-21
ok, post the results.

Also I've had trouble in the past with the installer if I try to access my computer's hard drive from the live session.  Try just booting to the CD and installing right away without doing anything else first.  In addition, if you are trying to have the installer import your user settings from Windows, you might want to try installing without that option.

---

### Post by adamwe1012 on 2008-02-22
sorry, but how do u do that, i was out-and-about all day while the format happened and all went well but how do u install without going into the live cd?

---

### Post by pytheas22 on 2008-02-22
> how do u install without going into the live cd?


Sorry if I was unclear--I was posting late--but all I meant is that you should boot to the live CD and begin the install right away once the desktop loads--don't try doing other stuff like viewing your Windows partition (if you have one) or playing with Firefox, et cetera.  I'm not sure if you did this before, but it could be the source of installer problems (if you mount a partition and the installer can't unmount it and stuff like that).

---

### Post by adamwe1012 on 2008-02-22
ughhhhh, well now another problem :confused:. Now when i got to press forward for the first time(right after i choose ENGLISH) it will just lock up, the CD is still spining and the HDD light comes on and off(in no pattern), any ideas. Also i really appericate all this help w/ my probs.

---

### Post by pytheas22 on 2008-02-22
There's something strange going on if you're getting inconsistent, erratic behavior like this.  Did you check the CD for defects?  I can't think of what else would cause problems like that, since all of your hardware should be pretty standard.

If you can verify that your CD is not corrupt, another option would be to burn the alternate install CD and try that instead.  The installer is in text mode but it uses less memory and so on, which might be important because I looked up your computer model and it appears to be rather old--how much memory does it have?  An iso is available here [http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso) .  If that download is slow you could choose another mirror.

Also what are the specifications of your computer in general (processor, memory, und so weiter)?

---

### Post by adamwe1012 on 2008-02-23
k well nvm i got it to work it was because i have a horrible cd drive in there cuz the fixed one broke.  I put a swap partition on it and it worked like a charm(im on it right now haha)
anyway, it has 256 ram umm 32 vid ram, and a 800Mzh intel III cpu, and a 20gb hdd, not to good but hey i got it for free cuz the owners thought it was busted but it just needed a new power cord =P.  Also im stuck using 800x480 resolution, but where was this file u wanted me to get?

Edit: k i looked back at past posts and found it here it is

---

### Post by pytheas22 on 2008-02-23
ok, glad you got it installed.  Does everything work alright now--no more choppy screen--or are there still issues?

As for the resolution, your xorg.conf file is set up to allow 1600x1200 (seems big for an older computer but I guess it's possible) so I don't know why it will only give you a low resolution.  Did you try changing it in System>Preferences>Screen Resolution or reconfiguring X using the System>Administration>Screens and Graphics utility?  (if you use the latter, it would be a good idea to backup xorg.conf first as per the instructions at the end of this post).

As another option, as I mentioned earlier, there are two versions of Linux drivers for ATI video cards, an open-source one and a binary one.  By default Ubuntu uses the open-source driver, which I think is in many respects superior.  But you could try installing the proprietary driver in order to get a higher resolution; directions are here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).  I'm not positive that it will work for you though (your card might be too old to be supported) so make sure you backup your configuration first with the command```


cp /etc/X11/xorg.conf ~/Desktop
```

then if you run into problems and your computer can't start the graphical interface, you can type from the command line

```
sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf
```

to go back to the original settings.

---

### Post by adamwe1012 on 2008-02-23
ahhhhhhhh, the 2nd one worked. It is running twice as fast as xp, also i dont have to worrie about any virus problem thank you sooo much pytheas22!

---

### Post by pytheas22 on 2008-02-23
nice, enjoy Ubuntu!

---

