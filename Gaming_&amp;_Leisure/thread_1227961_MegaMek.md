---
title: "MegaMek"
date: 2009-07-31
forum: Gaming &amp; Leisure
---

### Post by recrispi on 2009-07-31
Hello!

As I haven't found any information in these forums about MegaMek I just wanted to let you all know about it.
It's a PC implementation of the Battletech boargame. It runs on java, so it should be multiplatform and the project is opensource :D
Here is the webpage o the project:
[http://megamek.sourceforge.net/idx.php?pg=main]("http://megamek.sourceforge.net/idx.php?pg=main")

Anyway, I managed to run it once within a XP VM, but I've had no success running it anywhere else (Ubuntu and real XP machines). :confused:
I get the following error:
"Could not initialise: java.lang.reflect.InvocationTargetException"
I know it's a java problem, but I don't know how to fix it.:-?

If anyone wants to try the game and manage to fix the problem I would be very thankful.\\:D/ :biggrin:

---

### Post by Grishka on 2009-07-31
maybe you're using icedtea, install [Java runtime environment](apt://sun-java6-jre), and simply run MegaMek.jar with it.

---

### Post by recrispi on 2009-07-31
Thanks!
I'll take a look at it tonight
:)

---

### Post by eragon100 on 2009-07-31
> **Grishka said:**
> maybe you're using icedtea, install [Java runtime environment](apt://sun-java6-jre), and simply run MegaMek.jar with it.

I have that package installed, but my default java is still icedtea.
How do I reconfigure the system to use the sun-java6-jre for java applications? Running dpkg-reconfigure operations on the packages doesn't help :(

EDIT: Problem solved, if anyone else has this problem simply type

sudo update-alternatives --config java

into a terminal and select the alternative that includes "sun" in the name :wink:
Then you will be using the official sun java package by default for java applications, which will also make a number of other java programs work, an example of which is frostwire.

---

### Post by Grishka on 2009-07-31
> **eragon100 said:**
> I have that package installed, but my default java is still icedtea.
How do I reconfigure the system to use the sun-java6-jre for java applications? Running dpkg-reconfigure operations on the packages doesn't help :(

EDIT: Problem solved, if anyone else has this problem simply type

sudo update-alternatives --config java

into a terminal and select the alternative that includes "sun" in the name :wink:
Then you will be using the official sun java package by default for java applications, which will also make a number of other java programs work, an example of which is frostwire.

yes. :) or use [galternatives](apt://galternatives), if you prefer gui apps over terminal.

---

### Post by recrispi on 2009-07-31
Hi!

I had installed java6-jre but not icedtea. So that wasn't the problem.
Anyway eragon100's answer solved my problem magically :D
Thanks a lot to everybody!
Enjoy the game

---

### Post by eragon100 on 2009-08-01
> **recrispi said:**
> Hi!

I had installed java6-jre but not icedtea. So that wasn't the problem.
Anyway eragon100's answer solved my problem magically :D
Thanks a lot to everybody!
Enjoy the game

You're welcome :wink:

---

### Post by ironnerd88 on 2012-08-12
I know I'm reviving a dormant thread, but I didn't think I really needed to creat a new Megamek tread since this one already exists.

I am using Ubuntu 12.04 LTS, and am having difficulty running Megamek 0.35.31.

I downloaded the Linux version from the Megamek site
I unziped the folder.
I installed java JDK 7
I marked the mgemek.jar fie as executable.

Now I can get part of the menu screen - ony buttons, no graphic.
When I click dtart new game, it asks for my name - I type that in and get the attached error:



Any help out there

---

### Post by overdrank on 2012-08-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

