---
title: "Blue screen in video playback"
date: 2006-02-09
forum: Desktop Environments
---

### Post by myluckismany on 2006-02-09
Hey all, i'm fresh to the forum. I just installed breezy on my laptop (Toshiba Satellite Pro 4300). All was well untill today. I went to play a dvd, and all i got was blue screen in totem. Tried it with xine, same thing. i've searched for solutions and tried them all, but nuthin. Any assistance would be great!

---

### Post by el3ktro on 2006-02-09
You have to install the necessary codecs. They easiest thing would be to use the "Automatix" script which installs some multimedia stuff. You could also just enable the universe, multiverse & backports repositories in your sources.list and install "libdvdcss2" which is needed to decrypt DVDs (they're encrypted).

Tom

---

### Post by myluckismany on 2006-02-09
I've already done all that. It was working this morning, now it's stopped :S

---

### Post by NoNo_231 on 2006-02-09
Does your system read the dvd? Does it mount it? Do you have the icon of the drive on your desktop? Does it play other DVDs? 
I have a DVD that I can play. Under windows it is autorun and asks me to install a player. However under linux I didn't find a way to overcome with it. To say the truth it isn't even mounted.

---

### Post by myluckismany on 2006-02-09
Sorry, i didn't specify. The dvd is detected and plays. i get audio. but no visual, just blue. This also happens with any other video format. Another thing, even when i open up a player (totem, gxine etc) it just shows blue. It's really weird. I've re-installed packages, re-configured my display (this did nuthin, although, it fixed up a resolution bug! i can now get 1280x1024 for my LCD) but yeh, i really have no idea how to fix it.

---

### Post by rudeboyskunk on 2006-02-09
this happened to me when i first used linux on my laptop.  it was a resolution problem, as soon as i set the correct resolution there was no more blue.  but it seems you've already done that, and the codec thing.  get a new graphics card?

---

