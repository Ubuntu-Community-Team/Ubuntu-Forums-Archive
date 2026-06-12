---
title: "GTK apps in KDE 4.2.3 lock the system..."
date: 2009-05-10
forum: Desktop Environments
---

### Post by Izobalax on 2009-05-10
I've had this problem ever since I've installed Kubuntu Jaunty. First, a little story...

I initially thought that this problem was AmaroK, as the system would frequently hang whenever I used Amarok. I used a different media player but the problem still remained. 

To cut a long diagnosis short, I THINK the problem is GTK. It's MOST notable when I'm using GIMP - I can pretty much guarantee that if I'm using GIMP my system, *at any random time during use*, will freeze when using GIMP. The freezes are different as well; sometimes I can only move the mouse and nothing responds, or EVERYTHING locks, or X just logs me out. Really strange. I've stopped using Firefox as well because that was causing the same problem. 

Essentially, with only Qt apps open, there are no problems. As soon as I wap out a GTK app, my system goes spazzy. 

What the HELL is going on and how can I solve this?

/izo\

---

### Post by Izobalax on 2009-05-11
Bumparoo!

/izo\

---

### Post by jadedoto on 2009-05-11
I'm experiencing the same problem. I noticed it with Firefox first, and now with Rhythmbox. Jaunty with KDE4.2.3

---

### Post by Izobalax on 2009-05-11
> **jadedoto said:**
> I'm experiencing the same problem. I noticed it with Firefox first, and now with Rhythmbox. Jaunty with KDE4.2.3
Thank god someone else has this!

I don't mean this in a bad way. 

/izo\

---

### Post by jimbo99 on 2009-05-12
Where did you get KDE 4.2.3 to install?

---

### Post by kde4-core-user on 2009-05-12
> **jimbo99 said:**
> Where did you get KDE 4.2.3 to install?

[http://www.kubuntu.org/news/kde-4.2.3](http://www.kubuntu.org/news/kde-4.2.3)

---

### Post by Izobalax on 2009-05-12
> **kde4-core-user said:**
> [http://www.kubuntu.org/news/kde-4.2.3](http://www.kubuntu.org/news/kde-4.2.3)
What he said. This is obviously frustrating, certainly for me, as I can't use GIMP without it crashing my system. 

/izo\

---

### Post by Monsieur Gonzalez on 2009-05-12
I have no problem here. Using Firefox all the time, Gimp on a daily basis, no crashes or freezes. 

Can you see any pattern? You have an Ati card, are you using the restricted drivers? 

If you launch the gtk app from konsole, can you see any 'strange' output?

Are you using qt-curve or gtk-qt?

---

### Post by Izobalax on 2009-05-12
> **Monsieur Gonzalez said:**
> Can you see any pattern?


It's pretty much guaranteed to lock in a random way when I click on something in the GTK app; it could be a window, a button to save or whatever. That action causes the lock up. Firefox is not so bad since it isn't STRICTLY GTK, but GIMP and others are definitely consistently problematic.

> **Monsieur Gonzalez said:**
> You have an Ati card, are you using the restricted drivers?


No, open source. 

> **Monsieur Gonzalez said:**
> If you launch the gtk app from konsole, can you see any 'strange' output?


I shall try that one. 

> **Monsieur Gonzalez said:**
> Are you using qt-curve or gtk-qt?


Qt-curve. I, at one point, also had gtk-qt installed and wondered whether that was conflicting with qt-curve at all, so I removed it. The problem remains. 

Curiously, since refusing to use ANY GTK app, my system hasn't crashed once. 

/izo\

---

### Post by Izobalax on 2009-05-12
OK, running GIMP in Konsole gives me this:

```
/usr/lib/gimp/2.0/plug-ins/refocus: error while loading shared libraries: liblapack.so.3gf: cannot open shared object file: No such file or directory

(gimp-2.6:4402): LibGimpBase-WARNING **: gimp-2.6: gimp_wire_read(): error
```

It was running, but I daren't do anything with the app in case my system died again. 

/izo\

---

### Post by Monsieur Gonzalez on 2009-05-12
> **Izobalax said:**
> OK, running GIMP in Konsole gives me this:

```
/usr/lib/gimp/2.0/plug-ins/refocus: error while loading shared libraries: liblapack.so.3gf: cannot open shared object file: No such file or directory

(gimp-2.6:4402): LibGimpBase-WARNING **: gimp-2.6: gimp_wire_read(): error
```

It was running, but I daren't do anything with the app in case my system died again. 

/izo\


Well, launching Gimp here I get no such message. Check the package liblapack3gf is installed. Though it might be unrelated to the crashes, but still, worth a try.

---

### Post by Izobalax on 2009-05-12
> **Monsieur Gonzalez said:**
> Well, launching Gimp here I get no such message. Check the package liblapack3gf is installed. Though it might be unrelated to the crashes, but still, worth a try.
It's installed.

---

### Post by Monsieur Gonzalez on 2009-05-12
Running out of ideas, but, does it happen with Desktop Effects disabled? Is Compiz installed? Some compiz config left? I'm running out of ideas, sorry...!!!

---

### Post by Izobalax on 2009-05-12
> **Monsieur Gonzalez said:**
> Running out of ideas, but, does it happen with Desktop Effects disabled? Is Compiz installed? Some compiz config left? I'm running out of ideas, sorry...!!!


Heh, no worries, man. I shall try no effects and report back. Compiz is not running or installed. 

Thanks for the help in any case! Curiously, Qt libraries have just updated. 

/izo\

---

### Post by Izobalax on 2009-05-13
> **Izobalax said:**
> Heh, no worries, man. I shall try no effects and report back. Compiz is not running or installed. 

Thanks for the help in any case! Curiously, Qt libraries have just updated. 

/izo\
Tried GIMP last night with about 15 minutes with no crash. Shall work on it more later, along with Firefox and see if the problem remains. 

/izo\

---

### Post by jimbo99 on 2009-05-13
> **kde4-core-user said:**
> [http://www.kubuntu.org/news/kde-4.2.3](http://www.kubuntu.org/news/kde-4.2.3)

Please do NOT direct me to KDE or kubuntu.org.  This is simply just an appeasment answer.  I was looking for the link to the repository for jaunty that allows for the upgrade.  I specifically asked for kde 4.2.3 so that was an obvious inference.

Sheesh, some people.

---

### Post by james_xxx on 2009-05-14
jimbo99, what in the world are you talking about? 

The person gave you a link to a page containing VERY PROMINENTLY the line that needs to be added to your sources.list, in order to upgrade to KDE4.2.3. This was no 'appeasement', and no one could have been more helpful.

At any rate, I was curious as to whether anyone else out there was having issues after having performed this upgrade. Is it safe to proceed?

---

### Post by Izobalax on 2009-05-15
> **Izobalax said:**
> Tried GIMP last night with about 15 minutes with no crash. Shall work on it more later, along with Firefox and see if the problem remains. 

/izo\
> **james_xxx said:**
> jimbo99, what in the world are you talking about? 

The person gave you a link to a page containing VERY PROMINENTLY the line that needs to be added to your sources.list, in order to upgrade to KDE4.2.3. This was no 'appeasement', and no one could have been more helpful.

At any rate, I was curious as to whether anyone else out there was having issues after having performed this upgrade. Is it safe to proceed?


OK, well, I installed the liblapack3gf development packages and, like I said, the Qt libraries updated themselves as well. 

I only have gtk2-engine-qtcurve installed. 

I used GIMP for a good half an hour or more the other night with no crashes of locks. 

Problem solved? I hope so. I wonder if it was a bug in the Qt libraries that didn't speak nicely with GTK...

/izo\

---

### Post by Izobalax on 2009-05-21
> **Izobalax said:**
> OK, well, I installed the liblapack3gf development packages and, like I said, the Qt libraries updated themselves as well. 

I only have gtk2-engine-qtcurve installed. 

I used GIMP for a good half an hour or more the other night with no crashes of locks. 

Problem solved? I hope so. I wonder if it was a bug in the Qt libraries that didn't speak nicely with GTK...

/izo\
Scratch that. Just had a series of locks when using GIMP again. Mainly on image-intensive work. 

**sigh**

/izo\

---

### Post by krazyd on 2009-05-24
This sounds like a memory problem to me. Both firefox and gimp thrash the RAM, and so the problem might not show up with other apps.

Try this: during boot, on the grub menu there is an item "memtest" or similar. Select that and let it run for 6 tests. If any errors show up, it means that you have a faulty memory chip and need to replace the bad unit.

---

### Post by Izobalax on 2009-05-25
> **krazyd said:**
> This sounds like a memory problem to me. Both firefox and gimp thrash the RAM, and so the problem might not show up with other apps.

Try this: during boot, on the grub menu there is an item "memtest" or similar. Select that and let it run for 6 tests. If any errors show up, it means that you have a faulty memory chip and need to replace the bad unit.
I shall try it. Thanks. 

/izo\

---

### Post by montesss on 2009-05-27
Izobalax you're not crazy and it's not your memory, so you can just forget about testing it.
I got the same issue and I can reproduce it with acute success :(
I am using GIMP intensively and did used it today too before I upgraded to KDE 4.2.3. After I upgraded it crashes beautifully, my screen goes blank, I get no errors in no logs. So tried to run it from console too... but screen goes blank.. can't see anything...

I have an ATI card and I use the normal drivers cause I can't use the proprietary ones (because... Jaunty... Xorg 1.6 :-x)

---

### Post by Izobalax on 2009-05-28
> **montesss said:**
> Izobalax you're not crazy and it's not your memory, so you can just forget about testing it.
I got the same issue and I can reproduce it with acute success :(
I am using GIMP intensively and did used it today too before I upgraded to KDE 4.2.3. After I upgraded it crashes beautifully, my screen goes blank, I get no errors in no logs. So tried to run it from console too... but screen goes blank.. can't see anything...

I have an ATI card and I use the normal drivers cause I can't use the proprietary ones (because... Jaunty... Xorg 1.6 :-x)


So I'm not going crazy. 

/izo\

> **krazyd said:**
> This sounds like a memory problem to me. Both firefox and gimp thrash the RAM, and so the problem might not show up with other apps.

Try this: during boot, on the grub menu there is an item "memtest" or similar. Select that and let it run for 6 tests. If any errors show up, it means that you have a faulty memory chip and need to replace the bad unit.


After the memtest, there is ONE bad memory address. 

/izo\

---

### Post by krazyd on 2009-06-03
> **Izobalax said:**
> 
After the memtest, there is ONE bad memory address. 

/izo\

One bad address is one too many. This is certainly the cause of your lockups, and it **will** continue to be a problem until you remove the bad memory module from your system!!

@montesss: this could be a completely different issue.

---

