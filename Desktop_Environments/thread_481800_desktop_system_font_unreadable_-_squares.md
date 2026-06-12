---
title: "desktop system font unreadable - squares"
date: 2007-06-22
forum: Desktop Environments
---

### Post by ubiqus on 2007-06-22
Hi,
major font problems here: the window title font, ubuntu's menu fonts, are unreadable, it's all squares. I don't know what led to this (this is my not-tech-savvy friend's computer, she doen't know what she did to it). 

Please see attached.

I tried to check language support for english, it seems to be enabled (I can't read because of the squares, so I counted on my machine which position does english have in the list, and went to this computer and counted; english is the only one enabled). 
Tried to change the font, to no avail, regardless of the font I choose.

Can somebody help?

It's Edgy, Intel.

---

### Post by ubiqus on 2007-06-23
Hello, anybody?

---

### Post by ubiqus on 2007-06-23
I'd appreciate any help I can get ...

---

### Post by elj4176 on 2007-08-13
me too. There are several threads about this same issue and no fixes??? 
This is similar to the famous bsod in windows. The gui is totally useless. The cli is still working and the server seems to be still serving pages but I'd like to use hte gui one in awhile.

---

### Post by jim_p on 2007-08-14
Well... It may be a dumb idea, but try regenerating the fonts cache

```
sudo fc-cache
or sudo fc-cache -fv
```

and see if it works

---

### Post by jamietssg on 2007-08-14
Same here. Characters on screen are all squares. Happened after updates. Any ideas?

---

### Post by elj4176 on 2007-08-14
I tried the command you listed and they both returned 'successful' but alas I'm still squared!

I'm not so upset about not being able to use the gui - what really bothers me is that i cannot update/upgrade/install/remove anything.
Aptitude/apt/synaptic all seem to be broken.

---

### Post by bwtranch on 2007-08-14
I was having some similar problems with gutsy about a week ago, not as bad as yours though. I think it was caused by some updates, but the latest updates seems to have fixed it.

Have you tried sudo apt-get update and what do you get?

Any bad entries in gedit /var/lib/dpkg/status   ?Like something failed or half-way installed?

---

### Post by Clay Ferguson on 2007-09-23
same with me guys... I just downloaded ubuntu  (ubuntu-7.04-desktop-i386.iso) and installed from the CD, and once it booted from the CD, which I was hoping was going to do an install, it went right to a login page, right away, after the GUI came up.  All the text on the screen was SQUARES.  It's a bit hard to read the screen when every character is a SQUARE.  ha ha.  ANYONE FOUND THE PROBLEM YET??????

---

### Post by mflint on 2007-10-03
Hey all,

This may be too late, but I just had the same problem. Solved it with the following:

```
aptitude search pango
```

... to find everything pango-like that's installed. Then I reinstalled them with:

```
sudo apt-get install --reinstall libpango1.0-0 libpango1.0-common
```

Then I killed X to restart it.

Hope this helps someone!

Matthew

---

### Post by CaptSpify on 2007-11-20
Thanks mflint!

It worked for me, Major props to you, good sir!

\\:D/

---

### Post by slotbumwaller on 2007-11-27
Matthew - you're a genius! This totally fixed it.

-Matt

---

### Post by motumboe on 2007-12-07
For me reinstalling pango wasn't enough.
I was compiling from sources pango and before the reinstall I had to go to the directory where I downloaded pango sources and I gave a 
```
sudo make uninstall
```

---

### Post by srijai on 2007-12-07
I am having the same problem with gnome desktop after upgrading from feisty to Gutsy. I tried reinstalling pango but still the problem persists.

---

### Post by srijai on 2007-12-14
Solved. I first deleted the files related to pango in usr/local/lib

Then I reinstalled pango. Now the display is fine.

---

### Post by andrek on 2008-01-01
I've tried mflint's and srijai's methods and it's still the same. What should I do ?

---

