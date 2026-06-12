---
title: "Can't get my games to work!"
date: 2012-03-11
forum: Gaming &amp; Leisure
---

### Post by srharri9 on 2012-03-11
I should start by saying that I've never used any versions of Linux before, and I've had Ubuntu installed on my computer for about 3 days now.  I love it--for the most part.  I would really like to keep it installed, but I'm getting very frustrated.  I understand that most games don't support any Linux version, but I've found instructions to get them to play.  However, when I follow them, they either don't work or I'm missing something I need to click on.

The two games I'm concerned with right now are Minecraft and Star Trek Online.

With Minecraft, I'm following these instructions:
[http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

However, when I try to tell the file to open with OpenJDK Java 6, the option just isn't there in the "open with" window, despite the fact that I have it installed (I think).

Star Trek Online is a mess.  I'm following the instructions listed here: [http://www.redshirtlinux.com/?p=122](http://www.redshirtlinux.com/?p=122)

I've followed the instructions to put the playonlinux helper in the correct folder, but I can't run it.



As I've said, I'm new here.  I'm not sure what other information to include to help you help me, but ANY help would be much appreciated.

---

### Post by Bölvaður on 2012-03-11
Lets check what (version) you have.
Open the terminal (if you have new version of ubuntu you can just click the super/meta/(windows) button and type in "terminal"

There type this:

```
java -version
```

This is the output I get when I write the instruction above:
```
$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

```


With the package I have installed it is automatically set up so that I can right click like it is described in the tutorial you are following, but if you have another version it is easy to overcome even if you cannot rightclick. Just dump the output of the command above and lets examine your options.



About startrack online:
> For additional help join the STO Wine Forum:

[http://forums.startrekonline.com/showthread.php?t=57815](http://forums.startrekonline.com/showthread.php?t=57815)
There is also a subforum of Gaming & Leisure that would probably be populated by people that can help you if you give them more info than you do here. [WINE forum]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

### Post by srharri9 on 2012-03-14
Thanks for the quick reply.  I appreciate the help.

Now, I was forced to put Windows back on the machine so I could have the computer in working condition for a school assignment.

I intend to put Ubuntu back on within the next day or two, so I will attempt the installs of these games then.  I miss it already, and it's only been a day!

---

### Post by pieman711 on 2012-03-15
Have you heard of dual booting. You can have both operating systems installed at the same time and decide when you turn on your computer which one you want to run. When you install Ubuntu it should give you the option to install it alongside windows on a separate partition.

---

### Post by srharri9 on 2012-03-15
I am familiar with dual booting, but this windows installation isn't working properly.  Lots of random weirdness :(

I'm going to go all or nothing ;)

---

### Post by srharri9 on 2012-03-16
Well, it turns out that I had installed Ubuntu 12 beta, and nothing was working right.  When I reinstalled this time, I installed 11 and everything is working properly.  All of the instructions I've found work fine.  Thanks for all the replies.

---

