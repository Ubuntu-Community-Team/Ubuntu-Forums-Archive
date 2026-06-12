---
title: "[elbuntu, Enlightenment DR17] Rather Strange Issue"
date: 2008-11-09
forum: Desktop Environments
---

### Post by Genotrius on 2008-11-09
Every now and then, my Elbuntu (Ubuntu using Enlightenment DR17) hits a wall and crashes, defaulting to a wall of code made up of the repetitive message here: [http://pastebin.com/m7f4e1260](http://pastebin.com/m7f4e1260) Is this something that is easily solved, or am I going to have to file a bug with Enlightenment?

Sometimes, before I get that message, my system will appear to run fine, but my keyboard seems to lag (I type too quickly and characters get left out) and I'm unable to start any new applications, though those that are still running usually don't have any problems.

---

### Post by Skripka on 2008-11-09
I ran e17 until last week, when the instabilities (on a fresh 64-bit install) just ticked me off enough to go back to something more mainstream.  E17 is still beta-officially 16.999.050 last I knew, it sure is pretty and can do beautiful things, but none of the DEs which sport is as a window manager have a large enough support or dev base for my tastes, when things go ill.


Have you posted a message to the devs or on an Elbuntu dev board?  That would be the 1st thing I'd try.

---

### Post by Genotrius on 2008-11-09
No, I haven't tried that. I'll post this there as well.
I really like Elbuntu and I've gotten very used to it now, so if I can find some way to fix this without having to learn a programming language, I'd really love to.

---

### Post by worldwithoutgurus on 2008-11-09
Hi,

Elbuntu is dead and no more maintained.

[http://e17blog.tuxfamily.org/](http://e17blog.tuxfamily.org/)

---

### Post by Genotrius on 2008-11-09
> **worldwithoutgurus said:**
> Hi,

Elbuntu is dead and no more maintained.

[http://e17blog.tuxfamily.org/](http://e17blog.tuxfamily.org/)

Well, it's not exactly Elbuntu as they were trying to develop it there, just Ubuntu Intrepid Ibex with the e17 packages from e17.dunnewind.net installed over it.
Do you know how to fix this issue, or whether it's user-fixable?

---

### Post by loell on 2008-11-09
I think you can only wait for  updates from the repo where you got it (e17.dunnewind.net).

compiling directly from CVS is another option.

---

### Post by Genotrius on 2008-11-10
> **loell said:**
> I think you can only wait for  updates from the repo where you got it (e17.dunnewind.net).

compiling directly from CVS is another option.

I'm not sure that an update would solve it, though. What I'm asking is if anyone knows whether or not this is an issue that can be fixed with some sort of a configuration file, or if it's strictly a problem with the content of the packages that I would have to patch their source and install them in order to fix.

---

### Post by loell on 2008-11-10
I don't think this is just a matter of config files, you can always delete **/.e**  to test if its a wrong config or not.

e17 core code is constantly updated, they either introduce a fix or made a new feature which eventually broke some parts of it, you could hardly apply a patch for it too, since the code itself has an unpredictable changes over time.

---

