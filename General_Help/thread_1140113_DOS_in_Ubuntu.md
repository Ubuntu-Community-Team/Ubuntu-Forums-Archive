---
title: "DOS in Ubuntu"
date: 2009-04-27
forum: General Help
---

### Post by GForsythe on 2009-04-27
Hello all.

I am blind, and so I heavily rely upon DOS and older systems to help me read what is going on.  Since I do a lot of writing, I use Word Perfect 5.1 as my standard word processing software.

I currently made the switch to Ubuntu to stay "up-to-date", since Windows is not very friendly to blind people.

I was wondering if there were anyway to get DOS working on Ubuntu, or at the very least, to get WP 5.1 to work.  I have done a lot of searching and can not find much about getting WP to work for Ubuntu.  Similarly, I could not find much about getting DOS to work on Ubuntu.  Does anybody know how to get this to work, or some kind of work-around?

Thank you

---

### Post by Morientes on 2009-04-27
The program called dosbox emulates DOS very well as far as I know.
I do not know if Word Perfect works on it. But it probably does.

EDIT: I can see there is something about Word Perfect here: [http://www.dosbox.com/wiki/Software:WordPerfect5](http://www.dosbox.com/wiki/Software:WordPerfect5)

---

### Post by mali2297 on 2009-04-27
There are two DOS emulators available in Ubuntu's repositories: **DOSEMU** and **DOSBox**. I don't know about WordPerfect, but it should work with DOSBox according to this [wiki page]("http://www.dosbox.com/wiki/Software:WordPerfect5").

EDIT: ...too late

---

### Post by benj1 on 2009-04-27
theres dosbox which is very slow, 486 games strugle on my 1ghz. dos emu is faster but harder to set up.

i don't know if i misread your post but if you just want dos because its text based, why don't you use linux's own terminal, youll have a much greater range of applications?

also are you aware ubuntu has a large print, high contrast theme in system-->preferences-->appearence-->theme?

---

### Post by cariboo on 2009-04-27
I have an old dos based service center program that I have to run every couple of years, it runs perfectly using dosemu. WordPerfect 5.1 will run in dosemu, as I tried it several years ago just out of curiosity. In my opinion, WordPerfect was one of the best word processors ever made.

---

### Post by Thelasko on 2009-04-27
> **benj1 said:**
> theres dosbox which is very slow, 486 games strugle on my 1ghz. dos emu is faster but harder to set up.

I've actually had excellent luck with dosbox.  I've managed to get Command and Conquer: Red Alert working better than it ever did in Windows/DOS.  You might have a setting wrong someplace.

To the OP:
If you use DOS most of the time, I would actually suggest [FreeDOS]("http://en.wikipedia.org/wiki/FreeDOS").  You can even purchase a new machine from [Dell ]("http://www.dell.com/content/topics/segtopic.aspx/e510_nseries?c=us&cs=19&l=en&s=dhs")with it pre-installed.

---

### Post by benj1 on 2009-04-27
> I've actually had excellent luck with dosbox. I've managed to get Command and Conquer: Red Alert working better than it ever did in Windows/DOS. You might have a setting wrong someplace.

i thinks its probably more that its graphics intensive games that ive tried, it does use need alot more memory tho, i had serious problems on my 500mhz 192mb machine, it all depends on the power of the op's machine and what theyre planning on doing i suppose

---

### Post by 3Miro on 2009-04-27
You can run freeDOS under VirtualBox. I tried setting it up once, but I was not very successful.

(and if you need dos for the ability to work without a mouse, the Linux shell is much better)

---

### Post by Thelasko on 2009-04-27
> **benj1 said:**
> i thinks its probably more that its graphics intensive games that ive tried...

I doubt your "486 games" are more graphics intense than C&C: Red Alert, which has a Pentium 1 minimum requirement.

P.S. You might have an incorrect [cpu setting]("http://www.dosbox.com/wiki/Dosbox.conf#.5Bcpu.5D") in dosbox.conf.

---

### Post by benj1 on 2009-04-27
> **Thelasko said:**
> I doubt your "486 games" are more graphics intense than C&C: Red Alert, which has a Pentium 1 minimum requirement.

P.S. You might have an incorrect [cpu setting]("http://www.dosbox.com/wiki/Dosbox.conf#.5Bcpu.5D") in dosbox.conf.

i will have to have a fiddle then (ive was trying to get rally championship working, best rally game ever:))

---

### Post by Thelasko on 2009-04-27
> **benj1 said:**
> i will have to have a fiddle then (ive was trying to get rally championship working, best rally game ever:))

I'm trying to find info on that game.  All I could find was "[Rally Sport]("http://www.dosbox.com/comp_list.php?showID=3395&letter=R")" with a note that says it runs slow.  It might be a compatibility problem with that particular game.

---

