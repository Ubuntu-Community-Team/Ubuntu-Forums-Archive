---
title: "Ubuntu lags competition on Screen Resolution"
date: 2007-03-17
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-03-17
Would someone please explain what's going on?

Feisty 20070316, boots up in 1024x768 on an IBM NetVista, 2GHZ Pentium 4, 17"LCD, Intel 845 graphics chip.  It thinks the 17" LCD screen is an Elographics touchscreen(?), 1024x768 max and from working with xorg, Ubuntu doesn't detect how much graphics memory is available. 

I just downloaded Freespire Alpha, which is based on Feisty Alpha.  Screen comes up in 1280x1024x24, millions of colors.  Looks great.

How come, on the same hardware, the competitive Linux distros support high resolution Feisty doesn't: PCLinuxOS, Freespire (based on Feisty), Simply Mepis (Ubuntu base), Puppy, DSL, ...

What's wrong with this picture?  There are 5 computers on our LAN, and three of them have Intel 845 type graphics chip.  There have got to be tons of them out there.  Is there any plan for Ubuntu to support Intel 845  and detect the monitor like the others do?

Thanks, Jerry Amos:confused:

---

### Post by kvonb on 2007-03-17
Yeah, I agree, it's a little unfortunate.

However to get the most out of your screen until we have that level of functionality, what you need to do find the scan frequencies that your screen supports, either from the manual that came with it or search the net for the model.

They should give the horizontal and vertical rates, something like: 28-60, or whatever.

Then edit /etc/X11/xorg.conf and change the defaults to use your new set.

It's a pain, but it works :)

---

### Post by Henrik on 2007-03-17
Please read this [https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)

And file a bug here [https://launchpad.net/ubuntu/+source/xorg/+filebug](https://launchpad.net/ubuntu/+source/xorg/+filebug)

With logs and debugging info attached.

Thanks!

---

### Post by jerrylamos on 2007-03-17
Thanks, it's easy to find the correct screen resolution, memory, scan frequencies, etc.  Just boot Freespire or Simply Mepis or PCLinuxOS or ... and look at their xorg.conf vs. Ubuntu (Kubuntu Xubuntu haven't tried Edubuntu).  Of course, once booted the competition, might as well keep running them instead of hassling Ubuntu's xorg.

From looking at Feisty objectives the impression is load tons of fancy packages on while not looking after us "ordinary desktop computer users" as in "Official Ubuntu Book, Forward".  Well, O.K. I spent 42 years in IBM mainframe testing & development, however I'd like to get more of my acquaintences to try Linux to spread the base and hopefully get more linux device drivers and linux friendly internet video......  For "ordinary desktop computer users" on Feisty: persistent doesn't work, hardware video detection is behind competition, small anklebiters like shutdown on Edgy and Dapper turn off this computer but Feisty doesn't, Network Manager turns off the already running network card so the user has to activate it, ...  There are launchpad bugs for these.

Cheers, Jerry Amos

---

### Post by Henrik on 2007-03-17
> **jerrylamos said:**
> There are launchpad bugs for these.


Are they all marked as confirmed and have all the relevant logs and debugging information? Without the physical hardware and without the right data, there is not much the developer can do.

---

### Post by jerrylamos on 2007-03-17
Here's a reference to the bug on Launchpad with some further data:

"(medium) Bug #89590:  Feisty doesn't recognize 17" LCD screen"

Any other info that would be useful let me know.

Cheers, Jerry

---

### Post by jerrylamos on 2007-03-17
I found another reference to Ubuntu Feisty crashes with Intel graphics card in an otherwise complimentary article:

[http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured](http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured)

Cheers, Jerry

---

