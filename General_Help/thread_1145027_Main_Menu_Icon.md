---
title: "Main Menu Icon"
date: 2009-05-01
forum: General Help
---

### Post by augoldfinger on 2009-05-01
I upgraded to 9.04 :(

I went to edit everything the way I like it...Does anything work in Jackalope?

Main Menu Icon
```
gconf-editor
```
```
apps > panel > objects > object_0 
```
```
/home/USERNAME/mylocation/Gnome.png
```

It did not work. I have a blank main menu icon.

Am I doing something wrong?

---

### Post by ajgreeny on 2009-05-01
Perhaps you forgot to check the "Use custom icon" box on the gconf page.  See attachment.

---

### Post by augoldfinger on 2009-05-01
> **ajgreeny said:**
> Perhaps you forgot to check the "Use custom icon" box on the gconf page.  See attachment.

Thanks for the heads up!!!

Yes I did previously have that checked. This method worked for me in 8.04 LTS, but when I switched to 9.04 it no longer worked.

I did have a statement above wrong...I did not upgrade, but completely replaced the OS doing a full format & installing Junky Jackalope.

---

### Post by codeseer on 2009-05-01
> **augoldfinger said:**
> Thanks for the heads up!!!

Yes I did previously have that checked. This method worked for me in 8.04 LTS, but when I switched to 9.04 it no longer worked.

I did have a statement above wrong...I did not upgrade, but completely replaced the OS doing a full format & installing Junky Jackalope.

I haven't been able to get it to work in 8.10 either.

---

### Post by ajgreeny on 2009-05-01
Well it certainly is working on my setup.  Here's a pic to show it as I have it on 9.04, on a single panel at the bottom, not liking the two panel gnome default system, I always get rid of the top one.  I know, it's too like windows for some, but that's the way I like it!

---

### Post by augoldfinger on 2009-05-02
> **ajgreeny said:**
> Well it certainly is working on my setup.  Here's a pic to show it as I have it on 9.04, on a single panel at the bottom, not liking the two panel gnome default system, I always get rid of the top one.  I know, it's too like windows for some, but that's the way I like it!


How many Pixels is your panel?

---

### Post by augoldfinger on 2009-05-02
Got it!

I created another panel, changed the orientation properties to bottom & Voilà!

Anyone know how to add a power down feature to the main menu?

---

### Post by ajgreeny on 2009-05-02
> **augoldfinger said:**
> How many Pixels is your panel?
24, though I see you've done it now.
I'm working on hardy atm so I will look and see about the power down possibilities when I'm in jaunty next.

---

### Post by augoldfinger on 2009-05-03
> **ajgreeny said:**
> 24, though I see you've done it now.
I'm working on hardy atm so I will look and see about the power down possibilities when I'm in jaunty next.

Thanks ajgreeny,
I was wondering if possibly the pixel size may have had something to do with it, but I guess not mine is 32.

---

