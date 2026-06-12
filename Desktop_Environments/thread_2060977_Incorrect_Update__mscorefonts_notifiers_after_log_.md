---
title: "Incorrect Update / mscorefonts notifiers after log in"
date: 2012-09-21
forum: Desktop Environments
---

### Post by Horrid Troll on 2012-09-21
Hello!

Been playing around with Kubuntu 12.04 and it's going quite well, except for a couple of problems. One I really can't seem to work out is that I get a notification every time I log in that there are updates available (there's not) and this:

[img]http://i.imgur.com/BrhSM.png[/img]

I have the MS fonts installed (from the repos) and they show on libreoffice and on [www.flippingtypical.com](www.flippingtypical.com), but the notifications come up every time still.

I've tried doing a purge and reinstall, but it doesn't help..

---

### Post by oldos2er on 2012-09-21
Does ```
sudo dpkg --configure -a
``` help at all?

---

### Post by Horrid Troll on 2012-09-21
> **oldos2er said:**
> Does ```
sudo dpkg --configure -a
``` help at all?

Thanks for the reply =)

No, sorry, it accepted it without any output - tried rebooting and reinstalling mscorefonts and it comes up with the same error.

Did get me slightly excited though as I realised that Muon hadn't told me that some upgrade packages were being held back, so I dist-upgraded them...but still the same notifications.

I presume the 'Software upgrade notifications are available' message refers to the error with mscorefonts, as there's definitely nothing left to upgrade now =/

---

### Post by bra|10n on 2012-09-25
Do
```
sudo apt-get purge ttf-mscorefonts-intaller
```then
```
sudo apt-get update && sudo apt-get dist-upgrade
```then
```
sudo apt-get install ttf-mscorefonts-installer
```

---

