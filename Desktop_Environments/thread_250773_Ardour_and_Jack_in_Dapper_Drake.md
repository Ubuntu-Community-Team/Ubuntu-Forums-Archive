---
title: "Ardour and Jack in Dapper Drake"
date: 2006-09-04
forum: Desktop Environments
---

### Post by hurtstotalktoyou on 2006-09-04
Hi, all.  I'm very new to linux, though I have tried Ubuntu several times over the past year or so.  It's all so very different from Windows, and so the simplest of tasks gives me headaches up the whazoo.

What I want to do is run a program in Ubuntu similar to Adobe Audition (AKA Cool Edit Pro) for Windows.  Audition is, of course, a multitrack audio workstation.  This is key if I'm ever going to be a regular linux user, because I use Audition almost every day for some task or another.  I'm going to need a linux alternative, no bones about it.

As far as I can tell, the only comparable linux software to Audition is called Ardour.  Ardour, in turn, seems to require some program called JACK Audio Connection Kit for it to work.

Ardour is in my repositories, but it won't install for some reason.  There are several programs called "Jack something or other" in my repositories, but none which are called "JACK audio connection kit."  The download page for JACK only offers me the source code, which I don't know how to compile (though I'd love to learn).

So, what am I to do?  Are there any Dapper Drake users out there who have installed Ardour?  What's your secret?

Thanks in advance!

---

### Post by xyz on 2006-09-04
Well, first thing you could start doing is to go to the Ubuntu Studio, read a bit and ask questions if need be:
[http://www.ubuntuforums.org/forumdisplay.php?f=128](http://www.ubuntuforums.org/forumdisplay.php?f=128)

---

### Post by tenshi-no-shi on 2006-09-11
Have you enabled all the extra repositories? including multiverse? and also the backports? oh and the jack audio connection kit is jackd.

---

### Post by goldman on 2006-09-11
Hi, I don't know if the list of all repositories are in another topic. could you please help me about where can I find them?

thank you!

---

### Post by hw-tph on 2006-09-11
[Look here](https://help.ubuntu.com/community/Repositories/Ubuntu#what) for adding repositories.

The package you want is called *jackd* and is located in the "Universe" repository.


Håkan

---

