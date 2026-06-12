---
title: "Helvetica font"
date: 2009-01-08
forum: General Help
---

### Post by anjanesh on 2009-01-08
For some reason text on webapges using Helvetica font look ugly. Every letter is like 'smashed' against each other. I dont know the reason - if its rendering or not, but is there a way to get rid of Helvetica font ? Or replace it ?

---

### Post by kerry_s on 2009-01-08
helvetica is a bitmap font, run:
[B]
sudo dpkg-reconfigure fontconfig-config
[/B]
select no on bitmap
then run:

**sudo fc-cache -vf**

then restart X
your system will use ttf fonts.

---

### Post by nikgare on 2009-01-08
You may also want to have the standard MS fonts installed, this may help with some of the strange font choices made the the web developers:

sudo aptitude install msttcorefonts

---

### Post by anjanesh on 2009-01-10
That did not solve my problem. I already have msttcorefonts and bitmap set to off.
I had a number of ttf fonts loaded in my home folder - /home/user/.fonts
I removed these and now everything is working just fine. How can I know which of those fonts was causing the issue ?

Thanks

---

