---
title: "Fonts in Firefox are bit ugly"
date: 2005-07-13
forum: Desktop Environments
---

### Post by fbn on 2005-07-13
Hi,

I've attached a screenshot how Firefox looks on my Hoary installation.

The normal fonts are not perfect but okay but the headlines are too fat (bold) and look ugly.

I'm sure that this can be changed, I've tried some other fonts in the FF font configuration window but I was not pleased with any of them.

What are your font settings in FF or how can I make my fonts look better? :)

Regards,
  Frank

---

### Post by arnieboy on 2005-07-13
from terminal do a :
```
sudo apt-get install msttcorefonts
```
that shd make firefox look much better

---

### Post by torena on 2005-07-13
I've got a similar problem as well.  On pages with lots of text (like news sites) some of the lines will be half as tall.  If I highlight them they move to where they should be.  I'm using Kubuntu now but I had this problem with Ubuntu as well.  I'm not at home atm so I'll have to check if I have the same problem with Konqueror but either way I'd like to fix it. ;)

---

### Post by ttp on 2005-07-13
[QUOTE=fbn]The normal fonts are not perfect but okay but the headlines are too fat (bold) and look ugly.[/QUOTE]
That's what happened to me when I enabled the autohinter module. I had to disable it.

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

---

### Post by pt123 on 2005-07-13
I actually like the fatter fonts its easier to read and it looks better.

---

### Post by Curlydave on 2005-07-13
The ubuntu fonts in general look kinda not-so-hot to me, but that can be fixed. The problem is that they're just not even. They'll have some parts that are 2 pixels thick, some one pixel. It just looks sloppy.

---

### Post by fbn on 2005-07-14
I already have installed the msttcorefonts and some of the fonts listed on the Ubuntu Starter Guide (not all because I don't use asian or arabic fonts).

Is that enough already or do I have to configure FF to use some of these fonts? If yes which ones?

---

### Post by guitard00d on 2005-07-29
[QUOTE=arnieboy]from terminal do a :
```
sudo apt-get install msttcorefonts
```
that shd make firefox look much better[/QUOTE]

Appears that Kubuntu doesn't know where to find the msttcorefonts package. What do I have to hadd to my sources.list in order to download that package?

---

### Post by BanskuZ on 2005-07-29
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

@fbn: [http://www.ubuntuforums.org/showthread.php?t=20976&page=1&highlight=cleartype](http://www.ubuntuforums.org/showthread.php?t=20976&page=1&highlight=cleartype)  or [http://www.ubuntuforums.org/showthread.php?t=23426&page=1&highlight=cleartype](http://www.ubuntuforums.org/showthread.php?t=23426&page=1&highlight=cleartype)

---

