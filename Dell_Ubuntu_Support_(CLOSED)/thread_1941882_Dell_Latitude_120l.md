---
title: "Dell Latitude 120l"
date: 2012-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Meikrekel on 2012-03-16
Hello,

I've installed XBMCbuntu Eden beta 3 on an old laptop this morning. This laptop is a Dell Latitude 120l with a Sigmatel STAC 92xx sound card. I have connected the laptop to my TV with a VGA cable for the display and for the sound I've used a 3.5mm Jack to 2x RCA male. 

The problem is: my laptop does play sound by itself. But it doesn't play the sound when connected to my TV (so there comes no sound out of my tv, but when I unplug the 3.5mm jack, there does come sound out of the laptop). 

I've tried the following solution: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
But that didn't work (filled in for model: dell-m24).

Can anyone please help me?

Cheers,
Meikrekel

PS, sorry for my poor English

---

### Post by marinara on 2012-03-17
can you test with headphones?

---

### Post by Meikrekel on 2012-03-17
Yes I've tested that and strange enough sound does work trough the headphone

---

### Post by marinara on 2012-03-17
one theory is that the audio output is overdriving the audio.   Otherwise, it might be a problem with your tv.
I suppose your laptop could be detecting the tv and doing something wierd, but I doubt it.

---

### Post by Meikrekel on 2012-03-17
> **marinara said:**
> one theory is that the audio output is overdriving the audio.

If this is the case, how can I solve this?

---

### Post by marinara on 2012-03-19
after reading this thread:
[http://forum.audacityteam.org/viewtopic.php?f=27&t=6764](http://forum.audacityteam.org/viewtopic.php?f=27&t=6764)

it appears you only need a special cable when hooking up to microphone input.  So never mind about overdriving.

you need to check your TV.  (and cables) something is off.

---

### Post by Meikrekel on 2012-03-20
I've checked every option but still nothing.. What I don't understand is that my headset does work

---

### Post by gordintoronto on 2012-03-20
What version of Ubuntu is XBMCbuntu Eden beta 3 based on? What kernel does it have? Each recent version of Ubuntu has made improvements in sound control, specifically with the issue you have. If it's based on Ubuntu 10.04 LTS, that would explain your problem.

You could easily install the current Ubuntu and install XBMC inside it.

---

### Post by Meikrekel on 2012-03-21
I believe it's based on ubuntu 11.10, but I've also tried linux mint LXDE 12 and the sound doesn't work in there either..

---

