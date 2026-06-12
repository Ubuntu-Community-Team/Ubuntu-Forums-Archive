---
title: "Sound converter"
date: 2009-05-17
forum: General Help
---

### Post by mark.giblin on 2009-05-17
Having read an article on converting ogg to mp3 in ubuntu... I can say that I can play MP3's no problem in the various media players I have thrown MP3's at BUT...

The sound converter program does not allow me to convert ogg to mp3.

Before anyone rushes to correct me. THE "MP3" option is blanked out, it is not a selectable option.

SO... What am I missing off my install that will allow conversion.

Given that I can play MP3's, I am guessing that I am missing a library and if so what should I be looking for?

---

### Post by hyperdude111 on 2009-05-17
Try winff I think it converts oog to mp3 [http://winff.org/html/](http://winff.org/html/)

---

### Post by kpkeerthi on 2009-05-17
Install lame and try again.
```
sudo apt-get install lame
```

---

### Post by mark.giblin on 2009-05-17
OK, I went I did a repsitory and a used synaptic... Do not see winFF anywhere despite following the instruction first read then read while doing it... 

I then thought that if this has added the required library to convert to MP3, sound convertor should beable to use the library but it was still greyed out.

SO I guess that the procedure on the tutorial did no work. I much prefer to get Sound Converter working than add yet more software, but thanks for your suggestion.

Anyone know why or what I need as in a library or whatever you call them?

---

### Post by mark.giblin on 2009-05-17
Thx, kpkeerthi but here is my sudo line

sudo -gone right over my head, sorry

I have no idea how you would do that, I am new to Ubuntu and whilst using it as my main, not touched my WinXP in months other than to get settings for software I have found alternatives of, so working it and learning it is a learning curve and I am on the other side of the bell curve.

Old dog, New tricks.... O'Master

:D

---

### Post by mark.giblin on 2009-05-17
OK, I double checked everything and the winFF had not installed.

So I marked it and then applied the changes as before... it looks like its installing the winFF.

We shall see!

---

### Post by mark.giblin on 2009-05-17
winFF has now installed.

AND... MP3 is now an option in sound convertor...

Thanks for the heads up on the winFF, could prove to be the simpler option in dealing with this problem.

---

### Post by kpkeerthi on 2009-05-17
> **mark.giblin said:**
> Thx, kpkeerthi but here is my sudo line

sudo -gone right over my head, sorry

Make sure Universe and Multiverse are enabled under System -> Admin -> Software Sources.

Open System -> Accessories -> Terminal and write this command line
```
sudo apt-get install lame
```

or Use the easy way: Applications -> Add/Remove. Search for **lame** and install it.

---

### Post by mark.giblin on 2009-05-17
Thanks for the info but the install of winFF has sorted the issue out.

Think that this is a good way of dealing with this issue for people who have a similar problem.

Cheer.
M.

---

