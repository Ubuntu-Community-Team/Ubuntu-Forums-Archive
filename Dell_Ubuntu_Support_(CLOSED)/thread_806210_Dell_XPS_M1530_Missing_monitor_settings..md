---
title: "Dell XPS M1530 Missing monitor settings."
date: 2008-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aaBlueDragon on 2008-05-24
I'm running ubuntu 8.04 on my Dell XPS M1530.
I Can't use some screen modes in ubuntu, which i can use in windows xp.
like 1024x640 (it has widescreen)
or just using 60 hz on the same resolution that worked in xp, in ubuntu i don't have the choice.
the "Screen resolution" program seems to ignore the xorg.conf file and it doesn't dislay the correct monitor name.. it just says Unknown instead of Configured monitor.
have a look at the attached png pic.
i would also like to mention that i have updated to the latest nvidia drivers 169.21 and even warcraft 3 works fine in wine, so thats not the problem.
its just this monitor issue! please help!
Thanks in advance!

---

### Post by aaBlueDragon on 2008-05-24
any ideas anyone??

---

### Post by aaBlueDragon on 2008-05-30
Please somebody :confused:

---

### Post by sc00ter on 2008-06-04
What BIOS version do you have?

---

### Post by RedRat on 2008-06-07
I had the same problem.

Try downloading nvidia-settings. I think you can get it thru synaptic or apt-get.

When run it use the alt-F2 to bring up a terminal. then you have to type in"
gksudo nvidia-settings

It will ask for your password, if you don't do this, the xorg.conf cannot be saved because you need to be adminiter.

the nvidia-settings program will come up and you can chose whatever setting work for you and your monitor.

I found that when you bring down the System>Preferences>Screen Resolution applet, it does not seem to talk to the nvidia driver very well. But the nvidia-settings program seems to set the correct settings.

Hope this helps. Try searching the forum for nvidia-settings.

---

