---
title: "tremulous is open source?"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by rybu on 2007-09-16
I recently downloaded tremulous and have been playing with it on my new laptop.  I'm getting on average about 95 fps at 1920x1200 in 32-bit colour on my thinkpad t61p.  What an upgrade from playing Doom on my old 33MHz 486. Now my question.

I look at the tremulous webpage:

[http://www.tremulous.net/](http://www.tremulous.net/)

and it pretty clearly says Tremulous is <b>open source</b>. But the source is not available for download there.  A little more searching and I come across a sourceforge page:

[http://sourceforge.net/projects/tremulous](http://sourceforge.net/projects/tremulous)

but that source code is for an older version and hasn't been updated in a long time.  

Does anyone know where the repository for the current "stable release" (1.1.0-4) is, and where the current development snapshot is?

It's strange that the version that I can get from apt-get is more up to date than the one on the tremulous webpage or sourceforge repository.   I tried Googling for a while and came up with nothing.

---

### Post by Perfect Storm on 2007-09-16
Have you tried the CVS version? It's usually the source development codes.

---

### Post by Adrian_b on 2007-09-16
When you download the linux instaler and you execute it, it gives you an option to install the source with it too.

---

### Post by verb3k on 2007-09-16
I am sure this is what you want :
[http://svn.icculus.org/tremulous/trunk](http://svn.icculus.org/tremulous/trunk)
Here goes the current development of the game
Hope that helped :)
verb3k

---

### Post by rybu on 2007-09-17
Thanks verb3k, yeah that's what I was looking for.   It seems like the authors are hacks -- they don't document their work very well, or take advantage of any of the nice automated documentation packages available.  That's too bad.  But I guess that's how it goes.  

It appears that parts of the code are tuned for SMP compilation.  Have any of you tried to do that?  I see flags for it in the makefile for the mac distro. Would you use mpich if you were to do smp in linux, or is there another library?  the -lsmp flag, I don't know what library that is, or if it's available for linux. 

I can get the svn repository to compile on my system but the executable crashes.  Right now I'm running the standard version that you can get via apt-get with the standard ubuntu repositories.

---

### Post by Antonlacon on 2007-09-17
Tremulous is a modded ioquake3 based game.  You'll most likely have better luck with them if you have questions.

[http://ioquake3.org/?page=home](http://ioquake3.org/?page=home)

---

### Post by conehead77 on 2007-09-17
not sure if this is the answer to your question, but tremulous can be installed with the packet manager (using 7.04)

edit: rereading your post again and im pretty sure its not ;)

---

### Post by rybu on 2007-09-17
> **Antonlacon said:**
> Tremulous is a modded ioquake3 based game.  You'll most likely have better luck with them if you have questions.

[http://ioquake3.org/?page=home](http://ioquake3.org/?page=home)

Wow, thanks for the link.  That link contains a bunch of links to projects developed with the quake3 engine.  "World of Padman" looks great.  I've been away from computer games for almost 10 years now... what a change.   ioquake3 seems to be the source for information, and everything else.

---

