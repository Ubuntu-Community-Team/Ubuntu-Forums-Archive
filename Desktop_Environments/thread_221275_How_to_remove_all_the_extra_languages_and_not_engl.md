---
title: "How to remove all the extra languages and not english fonts?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by shawnrgr on 2006-07-22
I'm trying to slim this box down as much as I can. I have an 80gig hd but do alot of audio recording with audacity and adour which takes up truck loads of space. Is it possible to remove all the themes except for the one im using now and extra non-english language packs and fonts?

---

### Post by roostishaw on 2006-07-22
I think you can remove all the non-english (or whichever ones you want) language packs with localepurge.
Try:
```

sudo apt-get install localepurge
sudo localepurge

```
From then on, it will be run after every successful install using apt.

[http://packages.debian.org/stable/admin/localepurge](http://packages.debian.org/stable/admin/localepurge)

Tell me how it goes...

---

### Post by ardchoille on 2006-07-22
> **roostishaw said:**
> I think you can remove all the non-english (or whichever ones you want) language packs with localepurge.
Try:
```

sudo apt-get install localepurge
sudo localepurge

```
From then on, it will be run after every successful install using apt.

[http://packages.debian.org/stable/admin/localepurge](http://packages.debian.org/stable/admin/localepurge)

Tell me how it goes...

Wow, now that is an awesome app. I wish I had known about it when I first installed this system :)

Thanks for the URL :)

---

### Post by shawnrgr on 2006-07-22
that removed 12820K from the disk... thanks. what else can i delete? i've already removed packages like the ubuntu-examples. wich was like 20megs. there must be more usless stuff i can remove. Currently the system is taking up 16 gigs, with 1 gig being from my home folder.

I also have 75 total tasks\processes running not counting the webbrowser and the terminal. Doesnt that seem like alot?

---

