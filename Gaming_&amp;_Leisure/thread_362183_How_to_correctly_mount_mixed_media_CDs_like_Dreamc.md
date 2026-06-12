---
title: "How to correctly mount mixed media CDs like Dreamcast CDI"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by darkmaster on 2007-02-15
Hi everyone. I'm trying to correctly read with Ubuntu a Dreamcast backup game wich is a mixed data one. I don't exactly know how it is done but when I insert it in Windows, it shows me a lot of data while if I insert it in Ubuntu it reads it as a music cd only! That's not correct. How do I mount it correctly?

We're talking about a Disk Juggler .cdi masterized disk format, a backup game for dreamcast. Chankast, the dreamcast emulator, works fine under wine, very quick too, but the fact that Ubuntu reads my CD as a sound only disc, makes wine read it the same way too (Wine just reads what's mounted in /media/cdrom0).

There's another way you can help me too. The other way is: how do I mount a .cdi disc image in wine? Anibody managed to have wine run alcohool 120% or daemon tools?

I've tested another Dreamcast emulator, the name's Demul. This emulator can run iso images too (And cdi, nrg, ecc...) and it works under Crossover. Having it to read a .cdi game, the emulator worked fine but both under windows and linux it is unplayable, too slow. 

So, how can I mount correctly a mixed CD like this in Ubuntu? Any help will be very apprieciated! :)

---

### Post by Saturn Neptuni on 2008-12-24
I had a similiar problem and didn't find any answer around the web, instead, mostly unanswered questions asking for help. I don't know much about ubuntu (yet) or about pcs in general, however, after I installed and used a program called "Disk Management" (provided by the ubuntu comunity) to mount the cd with it, I could access the data contained and not just the audio files. I hope that helps.

---

### Post by dkrus on 2008-12-28
I have you tried acetoneiso it's about the closest I've seen to Daemon tools

---

### Post by TheIdiotThatIsMe on 2008-12-28
I own one of the original Dreamcasts were you could play backup games. Unfortunately, I asked a few times and all the answers I got were pretty much that CDI is not supported under Linux very well. I forget the technical reasons, cause there were problems with converting them to isos too. Your best bet for now may be under Windows.

---

### Post by bulletxt on 2008-12-30
CDI cannot be converted to ISO. ISO is a single track filesystem so the converted image will result in a loss of data. AcetoneISO also doesn't support direct mounting of CDI images. It can convert it to ISO but as said you will loose some important data and for sure the game won't boot.

As of today, the only solution under linux for such exotic images is CDEMU.
However, making CDEMU work isn't the easiest thing on earth.

The official website is:   [http://cdemu.sourceforge.net](http://cdemu.sourceforge.net)

---

