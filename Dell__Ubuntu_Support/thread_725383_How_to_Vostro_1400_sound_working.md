---
title: "How to: Vostro 1400 sound working"
date: 2008-03-15
forum: Dell  Ubuntu Support
---

### Post by louca on 2008-03-15
I got this working since this morning and then went and messed it up. Took forever to fix it.

I think those additional steps may have cleared it up for me why others weren't getting it to work.

**From a clean install here is what I did**:

```

sudo apt-get install linux-backports-modules-generic

```

Restart the computer
Once the computer restarts, it will not detect your sound card at all! Don't fret, type:

```

sudo gedit /etc/modprobe.d/alsa-base
```

**Then add this line to the end of the file:**

options snd-hda-intel probe_mask=1 model=3stack

**Save the file and reboot**

The sound should now be working through the speakers AND switch to the headphones once you plug them into the left jack. The problem where the sound still comes through the speakers and the headphones at the same time is not present.

**Problems:** Headphone jack on the right doesn't work.

----------------------------------

Note: If this still doesn't work, you can try this:

```

sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

Then reboot when it is done.

------------------------------------

Now something that I did after all of this because I was greedy and wanted both my headphone jacks to work.. was go and download dell's linux-backports-modules file.
Screwed up everything when I installed it. I had to go and download the proper file manually from the ubuntu package site.

The file name was:

linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386.deb

if all of the above hasn't worked for you and you have been "fiddling" you might have to download this file manually to your home folder and install it using this line:

```
sudo dpkg -i linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386.deb
```

From there, restart and add the line to the end of /etc/modprobe.d/alsa-base

It worked from there after a restart for me.

---

### Post by Somatik on 2008-03-25
Is this working for hardy?

---

### Post by Somatik on 2008-03-25
Sould be working right away

my machine did not boot using the generic kernel so I selected the 386 kernel but the restricted kernel modules were not installed by the updater...

So installing linux-restricted-modules-2.6.24-12-XXX should fix the problem

---

