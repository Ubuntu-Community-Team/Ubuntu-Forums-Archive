---
title: "I want to burn DVD-Audio in Linux"
date: 2006-09-18
forum: Desktop Environments
---

### Post by dwasifar on 2006-09-18
I burn DVD-Audio DVDs for my car.  This is the DVDA format, just so we're clear; not a DVD-Video format.

In Windows, I do this with a batchfile utility that runs from a DOS box and kicks off dvda-author, mkisofs, and a couple of other things.  Is there a cleaner solution for this in Linux, or a front end for it, or something?  Anyone done it?

Also, I will probably need something that converts .mp3 to .wav in Linux, and I'm sure plenty of people have opinions about that.

---

### Post by samkon on 2006-09-18
I opened "Add/Remove Applications" and search for "converter" and I saw a package for you called "SoundConverter". let you try..

---

### Post by TeaSwigger on 2008-01-31
And so would I.

All I've found is this: 
[http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)

Libraries for the format? It looks highly commendable but dauntingly so (over my head).

What is the state of support in Ubuntu for this format?

---

### Post by dwasifar on 2008-02-07
> **TeaSwigger said:**
> And so would I.

All I've found is this: 
[http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)

Libraries for the format? It looks highly commendable but dauntingly so (over my head).

What is the state of support in Ubuntu for this format?

Actually I found out how to do it shortly after posting that question.

Here's a good guide, including the dvd-audio sourceforge project and a patched mkisofs.

[http://ubuntuforums.org/showthread.php?t=324746](http://ubuntuforums.org/showthread.php?t=324746)

---

### Post by Tyke91 on 2008-02-07
you can also just get DOSbox for linux (add remove) and install the same batch file

---

### Post by dwasifar on 2008-02-07
> **Tyke91 said:**
> you can also just get DOSbox for linux (add remove) and install the same batch file
Actually I rewrote the batch files as shell scripts and they work a lot more efficiently.

---

