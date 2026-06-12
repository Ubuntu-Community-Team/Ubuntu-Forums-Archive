---
title: "Which software might I use for building electronic Circuits Diagrams in Ubuntu Linux?"
date: 2009-12-22
forum: Education &amp; Science
---

### Post by madmax.santana on 2009-12-22
Well, the subject is the question. Has an engineer or a student come across a very good alternative of Multisim?

Or maybe just a little less compatible, since for now I only want to build a circuit diagram for use in my report of the project.

---

### Post by Kevbert on 2009-12-22
xcircuit may be of interest. Take a look [[COLOR="Red"]here[/COLOR]]("http://opencircuitdesign.com/xcircuit/download.html") - there's an old .deb file for it (linked on the homepage) if you don't want to compile from source.
[[COLOR="Red"]This[/COLOR]]("http://coolarm.wordpress.com/2008/06/16/electronic-software-in-ubuntu-linux/") may also be of interest.

---

### Post by hsweet on 2009-12-23
qucs and ktechlab are pretty good and in the repository

---

### Post by ussndmac on 2009-12-23
Are you talking electronic schematics, pc board layout, or circuit simulation?

I am happy with Eagle for schematics and pc boards.

I am happy with LTSpice for simulations.

Regards

---

### Post by Chronon on 2009-12-23
I haven't used it but have heard good reports about kicad.

---

### Post by madmax.santana on 2009-12-25
I have tried several different softwares and one of them eagle. There is one problem in common, people!!!
I dunno how to use them.
I am not a developer, (well a novice programmer and an enthusiast maybe). So I do not understand at all how I have to put these software to use to build simulations and/or schematics fast and reliable...

Look the scenario is, I am used to a windows software called Multisim... It is great, really, if I can ignore the fact that it's ******* propriety software...
For those who haven't used it, I'll post a few screenshots.
Please click on them for a full view. It explains how I use this software and hints my requirements.

[[IMG]http://img193.imageshack.us/img193/4073/screenshotxplained1.th.png[/IMG]]("http://img193.imageshack.us/i/screenshotxplained1.png/")

[[IMG]http://img192.imageshack.us/img192/6711/screenshotxplained2.th.png[/IMG]]("http://img192.imageshack.us/i/screenshotxplained2.png/")

Obviously, it is very good. (Almost the same thing as drag and drop.)

Maybe eagle and other software are better than this. But the problem is, I dunno how to  use them... Probably I have to write a code and compile it just to test a small resistive circuit...

What I have noticed in GNU software is that, they are very complex and built-for-experts, no-nonsense and powerful software... You have to 'learn' using it first, which might be very tedious. But once you learn them, you find that there is no match for them... Whatsoever maybe the case, my conquest is on and I really need the help of community... Please recommend the best software for (I'm marking it) Electrical Simulation AND/OR Electronics Schematics Design software in Linux, and I shall start learning them...

---

### Post by madmax.santana on 2009-12-27
No replies yet!!!

---

### Post by Chronon on 2009-12-28
It isn't clear to me what advice you're after.  You seem to want to stick to what you know rather than exploring the options people have presented.  That's totally your call.  If you have a method for doing the work using Multisim then go ahead and use it.  (It appears that Multisim uses spice, BTW.)  Basically, it's up to you to weigh the benefits and costs of learning a new software package to do this work.

There might be a couple of suggestions in this older topic that haven't been covered here. [http://ubuntuforums.org/showthread.php?t=322499](http://ubuntuforums.org/showthread.php?t=322499)

---

### Post by madmax.santana on 2009-12-29
Hell yeah pal!!! I am jumpin' here to learn new software! I am obsesssssed wid computers dude... 

But I have a problem... I am a student as are many of the users of Linux... See I am already learning a few programs and I dont say that I cannot learn eagle or spice. I am learning but IN-THE-MEAN-WHILE i also need a few software which are not very complex to operate... 
I hope you understand when I gotta submit ma assignment, I cant tell the professor "sir I cant do it today since i am learning a new software!!!"

Yeah you are absolutely right, that's my call and I call for learning new software instead of sticking on the old rotten prop ones... But that needs time and I am bit lacking there!!! Anyway, my vacations are soon after the fall exams and I shall improve a lot in these vacations... It's really awfully magnificent of you guys to help me with finding good software for my mentioned purposes... I really love Ubuntu Community!

---

### Post by Chronon on 2009-12-29
> **madmax.santana said:**
> 
But I have a problem... I am a student as are many of the users of Linux... See I am already learning a few programs and I dont say that I cannot learn eagle or spice. I am learning but IN-THE-MEAN-WHILE i also need a few software which are not very complex to operate... 
I hope you understand when I gotta submit ma assignment, I cant tell the professor "sir I cant do it today since i am learning a new software!!!"

:)

Of course, sometimes it is necessary/preferable to be practical.

---

### Post by madmax.santana on 2010-01-05
Oh K!!! Semester is over and guess what guys? 
[SIZE=4][COLOR=Red]**I am in with some news for you... **[/COLOR][/SIZE]

I recently used the apt-cache to search anything related to science...
> apt-cache search scienceAnd it returned a lot of programs and suits... Among all them I saw a _science-electronics_ metapack... Guess what??? I installed the whole 992MB of software suits for electronics... Ha-ha
> apt-get install science-electronicsAlthough I do not recommend you install the whole metapack, (I did it just for fun, install and then uninstall)... But there are a few software which might be worth your checking... Here!

There is a software called "**Electric**"... Wasn't very convenient to use but right from the interface, you have the feeling that it's a powerful thing...

Then a "**gEDA Scematics Editor**" --- I found it marvelous... Although not very feature rich, but simply perfect just for designing a circuit diagram to include in your report ;)

Then there was "**KiCAD**" almost everyone knows about it, it's a bit complicated, but then, it's for pros.

Here comes another one "**KLogic**" --- for all those associated with digital electronics... I loved this software... It looks to me like a clone for "Digital Works" software for Windows which we use in Digital Logic Design labs to construct and simulate the digital circuits.

"**KSimus Circuit Simulator**" --- Again, I haven't yet dived into it, but seems fairly full of features...

"**Oregano**" --- Yo, I was looking for something like this when I started the circuit. Just install and have a look, you will know why I LoVeD it.

"**PCB Designer**" was another one in the pack, and the name says it all.

I haven't completely used all of the software, not even gone beyond a few clicks in most of these software. But since many of them are rarely found in Ubuntu forums when simulation, PCB or schematic designing is discussed, I guess you people should give them some time and then spread the word on how they work... Maybe a few of them are even better than widely acclaimed Eagle and Spice etc...
I don't know the exact package names for these software but they are all in repos for sure and you can get the package name if you google the software name... It seems like Ubuntu isn't lacking anywhere while it comes to Engineerings and Sciences...

---

### Post by Darktrax on 2010-01-12
gEDA is now becoming possible to seriously use as a industrial circuit tool.

Version 1:1.4.3-2 ships with Karmic, but I see 1:1.6.0-3 is now available to users of Debian Sid and Ubuntu Lucid.

If one has the stable 9.10 Karmic, is it possible to still use the latest package from Lucid? How does one do this?

---

### Post by alexfish on 2010-01-12
hi
may be worth a look

[http://appdb.winehq.org/objectManage...rsion&iId=9846]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9846")

also

Just Ran old Version of Tina under wine  ;; mentioned in earlier post  

seems ok / demos working up to now

---

### Post by rebeltaz on 2010-01-13
I've been using EagleCAD since it was first released for DOS and I now use the Linux distro. There is no programming to it, more like drawing. And I couldn't use any of the other schematic programs if I had to.

---

### Post by robert80 on 2010-01-14
You  can use pspice software for your work.

---

