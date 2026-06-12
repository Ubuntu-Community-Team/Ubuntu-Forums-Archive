---
title: "WoW, Teamspeak, and DSP-550"
date: 2007-07-10
forum: Gaming &amp; Leisure
---

### Post by Quasimodo316 on 2007-07-10
I've run through all the posts and faq's I can find and still seem to be stuck.  So here's the situation.

've got a machine running 7.04, a 8600gts, a Teamspeak server, the teamspeak client, WoW, and a Plantronics DSP-550 (usb headset).  I've got all of that working...seperately.  WoW gives sound through the headset, but not if Teamspeak is started first.  Aoss doesn't seem to work with it at all.  From some command I ran from a faq I found that this device (dsp1) only shows with 1 playback and 1 capture.  I think this is a alsa support issue but wanted to ask those with more experience with this.  
The teamspeak server works fine for other people and I've gotten both WoW and Teamspeak working under Aoss with another person's PC (standard headset with phono).  Am I stuck buying another card rather than getting this 550 to work?  All assistance would be greatly appreciated.

---

### Post by slavik on 2007-07-10
dsp-500 here as well ... same issue but with ventrilo. also, getting enemy-territory sound is difficult, and if I use aoss sound is choppy ...

btw, how did you find out which device it was assigned to?

---

### Post by Quasimodo316 on 2007-07-10
I think the first time I just used > ls /dev/*dsp* to show me which ones were available.  I later used a code in a FAQ somewhere...I'll look for it and edit it back here if I can find it.


EDIT: Here's a link that told me directly: [http://ubuntuforums.org/showthread.php?t=492175](http://ubuntuforums.org/showthread.php?t=492175)
 and here's the faq that gave me the several commands to find out about it: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

---

### Post by Quasimodo316 on 2007-07-11
Anyone know if Alsa compatablility would cause this problem?  Or if Alsa doesn't support USB soundcards?

---

