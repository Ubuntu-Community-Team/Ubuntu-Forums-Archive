---
title: "Amarok Freezes"
date: 2006-07-06
forum: Desktop Environments
---

### Post by mthaddon on 2006-07-06
Hi Folks,

I'm close to having to ditch the excellent Amarok because it's freezing on me. It runs fine for about 20-30 minutes, and then it just freezes. Can't even initiate a shutdown without killing the amarok processes.

Anyone else experiencing this? How do I diagnose what's wrong?

Cheers, Tom

---

### Post by barbarian on 2006-07-24
Yes, occasionally it happens when i play last.fm radio stations for example..:(
I don't know the reason, probably Xine engine bug..

---

### Post by castironpants on 2008-04-26
I'm having this same problem, and I'm using Hardy.

---

### Post by mlissner on 2008-05-08
I had the same in Hardy as well. Try going into Amarok > Settings > Configure Amarok > Engine, and change the Output plug in to Alsa. 

I theorize this has something to do with PulseAudio, which is the Output plug in that I think is getting selected when Automatic (the default) is selected.

I just switched to Alsa, and so far so good.

---

