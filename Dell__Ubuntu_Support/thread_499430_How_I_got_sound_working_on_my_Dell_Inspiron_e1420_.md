---
title: "How I got sound working on my Dell Inspiron e1420 laptop with Feisty (7.04)"
date: 2007-07-12
forum: Dell  Ubuntu Support
---

### Post by DaveTRG on 2007-07-12
It took me awhile to figure this out, so I thought it might help someone else.  I purchased a new laptop with Vista (because they didn't have the video card I wanted offered with Unbuntu :() and immediately wiped it to install Feisty.  Out of the box, sound appears to work (no errors) but there was no sound.  Here's how I ended up fixing it:

To get sound working on the Sigmatel STAC9228 included with the new Inspirons, add the line:

```
options snd-hda-intel model=3stack
```

to the **/etc/modprobe.d/alsa-base** file by pressing Alt+F2 and typing

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then add the line to the file, save and reboot.

This site lists other “model” options for those of you having the same problem on different hardware:

[https://answers.launchpad.net/ubuntu/+source/ekiga/+question/7586](https://answers.launchpad.net/ubuntu/+source/ekiga/+question/7586)

Here are the specifics from that post:

options snd-hda-intel model=XXX

With XXX from this list:
   6stack *6-jack*
   6stack-dig *ditto with SPDIF*
   3stack *3-jack*
   3stack-dig *ditto with SPDIF*
   laptop 3-jack *with hp-jack automute*
   laptop-dig *ditto with SPDIF*
   auto *auto-config reading BIOS (default)*

From reading other posts, I believe there are other "model" options not listed such as "fujitsu" & "toshiba" so you may want to try Googling for more if none of those work.  

Of course, before trying any of this, ensure that the volume is up, etc ;-)

---

### Post by bakketti on 2007-07-24
It worked! :)

Thanks for the tip! I've been looking through posts all week trying different things and this one finally worked!

---

### Post by nutrapi on 2007-10-25
super awesome. great job. I can now resume studying while listening to music (new radiohead album isn't half bad).

---

### Post by nutrapi on 2007-10-25
BTW - this fixed my vostro 1400 in 7.10 gutsy! Not just a fiesty fix.

---

