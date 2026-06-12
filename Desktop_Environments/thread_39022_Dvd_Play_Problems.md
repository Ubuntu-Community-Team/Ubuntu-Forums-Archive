---
title: "Dvd Play Problems"
date: 2005-06-03
forum: Desktop Environments
---

### Post by lworrell on 2005-06-03
I have install Ogle and the Okle portions into the system along with all of the support files needed to run them (per the Ogle website).  The system is set up to see the DVD player in the /DEV directory and I still can not get the DVD player to play the DVD's.  Is there something I am missing here?

---

### Post by kubuntuuser on 2005-06-03
You need libdvdcss/libdvdcss2 I forget which one I installed but know this library is needed. From what I remember you will have to google it as it isn't in the repositories and you may need to compile it. 

You may also need to do 

sudo hdparm -d1 /dev/dvd    
# I think this is the command but am not at my linux box so cant tell you exactly.

before you play a dvd. This enables dma to your dvd drive and stops jerky playback. 

You can edit a config file somewhere though to make the change more permanent, again i am not at my linux box so cant tell you exactly. 

I use kaffine to play DVDs but also have dvds working in totem and many other media applications.


Just thought I'd get you on the right track, googling it the stuff here should turn up some forum responses.

---

### Post by lworrell on 2005-06-04
:) Thanks for the help.  It works fine now.

---

