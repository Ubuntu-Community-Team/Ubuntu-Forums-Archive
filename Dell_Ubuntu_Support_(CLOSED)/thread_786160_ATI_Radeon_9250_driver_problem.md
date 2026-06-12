---
title: "ATI Radeon 9250 driver problem"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by srcw0rm on 2008-05-07
I have a ati radeon 9250 installed on my computer and i cant seem to find the right drivers for it. especially ubuntu 8.04, how do i install them?and where are the drivers?because i tried most of them.please and thanks

---

### Post by jamesjohnson on 2008-06-04
Yeah i have been having the same problem.  I am new to Ubuntu and i tried just about everything, i heard that the ati 9250 wont work with Ubuntu.  I got as far as putting the catalyst control center on there but of coarse its not working.  So if anyone can figure this problem out let us know!

---

### Post by silvestros on 2008-06-04
You can try with Envy (if you haven't tried it). It's an application that automates the installation of ATI (and Nvidia) driver. It's very easy to use it. The link is:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good luck!

---

### Post by jamesjohnson on 2008-06-04
Yes i tried Envy and it told me that its not supported.  Which blows!  I mean i hate Microsoft with a passion, but open source is such a pain in the *** because you cant just click and watch it work OH NO NO, YOU HAVE TOO GET A SCRIPT THAT LOOKS LIKE CHINEESE TO LOAD ANYTHING, AND THATS IF THE SON OF A BITCH WORKS RIGHT, AND IF YOU WANT TO EVER UNINSTALL IT, HOLY **** I STILL DON'T KNOW HOW TO DO THAT!

---

### Post by Paul S on 2008-06-04
> **jamesjohnson said:**
> Yes i tried Envy and it told me that its not supported.  Which blows!  I mean i hate Microsoft with a passion, but open source is such a pain in the *** because you cant just click and watch it work OH NO NO, YOU HAVE TOO GET A SCRIPT THAT LOOKS LIKE CHINEESE TO LOAD ANYTHING, AND THATS IF THE SON OF A BITCH WORKS RIGHT, AND IF YOU WANT TO EVER UNINSTALL IT, HOLY **** I STILL DON'T KNOW HOW TO DO THAT!

You ought to direct your flame toward ATI, who provide the driver.  Envy is just a volunteer's effort to make it easier to install it on hardy.  The lack of driver support has nothing to do with the volunteer's script.

Check the AMD / ATI web site and linux driver status at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

I don't see 9250 listed .. (yet).

hth

---

### Post by a-converted-sparky on 2008-06-06
I am running the card as well, i can enable compiz etc etc, but performance is next to rubbish, max screen res is only 1280x1024 too :0(

you are correct envy wont install the driver as the legacy one works fine.

Guess we will have to wait for further devolpment/support

---

### Post by spoolboyy on 2008-06-17
@ JamesJohnson:  Don't confuse one's lack of familiarity with an operating system to be a poor design.  And yes, ATI is the devil in the open source world as Paul said, but I don't need much of a graphics card and I already have this one, so I'm trying to use it.

I am having this problem as well.  In fact, I can't even find a generic driver to download in 8.04.  Also, the card doesn't show up in "Restricted Drivers" for me so the walkthrough provided on the Ubuntu site does me no good. 

I had it working and then, of course did some tinkering to try and get the s-video out to work and ruined what driver installation I did have.  That's what I get for not backing up.  

Its a relatively new installation and would simply be faster for me to just reinstall linux (i have separate home and / partitions so my newly transferred data wouldn't need to be overwritten.).

I tried Envy and now the max res I can get to is 800x600 (which is killing my eyes right now).  I just want to reset it to the original driver that I got when I installed last night.

Any tips on how i can a list of basic ati drivers from the repositories?  I'm sure I'm just missing something....

-adam

---

### Post by Rocket2DMn on 2008-06-17
That Radeon 9250 is too old to be using the restricted fglrx drivers, they do not support cards older than the 9500 or so.  You should remove fglrx.  IF you installed with EnvyNG, you can remove them from there.  The .run file from ati's website may have an unistall option, or you may be able to start it with something like
```
sudo thefile.run --uninstall
```
Otherwise, try
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then you need to reconfigure X with 
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
and restart X with CTRL+ALT+BACKSPACE.  I think most people have had success with this card + compiz by following these directions to enable cards using the open source "ati" drivers for compiz - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
I have seen a few posts about people having trouble with the 9250, though.  Good luck.

---

