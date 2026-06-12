---
title: "Intel HDA sound not working, need some help."
date: 2006-09-04
forum: Desktop Environments
---

### Post by IanthePez on 2006-09-04
I am using the Intel d915pbl motherboard and I am having no luck getting my sound to work AT ALL.  I did the usual of going through and checking for anything that is muted, and that doesn't seem to be the case.  The module snd_hda_intel is loaded correctly it seems.  I even went as far as to try and update alsa, but I'm not sure I did it right...

I downloaded the newest version from alsa-project and simply did a ./configure, make, make install, make clean, and then restarted.  Is there more I have to do for this.  This is very frustrating as I just want it to work.  Any help would be much appreciated.

"lspci -v | grep -i audio" show the following
```
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
```

"lsmod" shows the following sound related things
```
snd_hda_intel          20120  1
snd_hda_codec         164400  1 snd_hda_intel
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81032  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    56164  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm
```

---

### Post by IanthePez on 2006-09-05
As much as I don't want to admit this, I thought I would say that I found the solution after much, much work.  When I took out my other sound card to switch over to the integrated one, I forgot one small step.  I didn't plug in the speakers.  Let that be a lesson to everyone to start with the basic stuff first, heh.

---

### Post by G2k on 2006-09-21
I have HDA intel as well and can't get any sound no matter what I do. I'm using a laptop so the speakers are plugged in by default. I've tried with all sorts of settings but alas no sound. Can't figure out what it is...

---

### Post by mstrat on 2006-09-22
Right there with ya, I've tried TONS of things, still no luck with sound in my Toshiba Satellite...Intel HDA sound card.  If there is someone with some simple instructions on how to re-update the drivers, I'll try again.  I've downloaded the stuff from alsa project, I think...though was somewhat confused on how to get it installed properly.  probably something simple like a 1d10t error.

---

### Post by Lord Illidan on 2006-09-22
I've had this happen to me on Fedora Core 5, recently.

The solution is go to this site and install the drivers from here :

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Further down the page is the Unix/Linux drivers.

Open the public version and untar it..and see what you can make of it. If you follow the readme you should be all set.

---

### Post by mstrat on 2006-09-22
I just tried this, it is also not my fix...any other suggestions?

---

