---
title: "java and firefox/epiphany/runescape"
date: 2006-08-03
forum: Gaming &amp; Leisure
---

### Post by Zyphrexi on 2006-08-03
Well i'm not a nooble by a long shot, but i've been having a hell of a time getting java to work with runescape either in firefox or epiphany.

I got most of my java-stuff set up with automatix, and i've been following [this guide]("https://help.ubuntu.com/community/Java") and it still comes up with a black area where the java app should be loaded. I know there is a great deal of problems surrounding getting rs to load in firefox, and i've heard that epiphany is easier, but in my case the problems are one and the same. 

I've exhausted all the resources I could get my grubby gamer paws on, and I'm at a complete loss. 

Any additional help would be greatly appreciated.

---

### Post by Zyphrexi on 2006-08-03
I solved the problem.

ran firefox in terminal with jsconsole enabled, discovered that the runtime parameter was incorrect (apparently I had modified that some time ago according to some post about 'speeding up' performance) Removed the parameter and tested, everything is good now.

---

### Post by ronourse on 2006-09-02
I am a noobie. I just installed the latest Ubuntu version 6.06.1 LTS. My kids love to play Runescape. I installed Java version 5 using Applications/Add and checked the "unsuported box. The installation seemed to go well and it appeared Java had been installed correctly. I go to the Runescape site using Firefox and try to play. It shows that necessary plugins are not installed (small blank screen with a small green puzzle piece).

It appears that other sites requiring Java are running correctly, but I cannot be sure. The kids play Runescape on another Windows machine and my Mac using Firefox with no problems.

What may be wrong here? I'm new to the terminal stuff, although I am an old DOS user, so with some instruction I should be able to fix something minor.

Any ideas?

---

### Post by ronourse on 2006-09-03
I got it to work. I was just "playing" around and went to App/Add/ Advanced and found "Mozilla Java Plugin 1.4" and installed it just to see what would happen. I started Firefox, went to Runescape and all is well. My oldest son is playing now.

Also, before I did this, I installed and ran Epiphany browser and the same problem existed.

Not sure what the difference is, but it now works.:D

---

### Post by dal2k5 on 2006-09-03
if u ppl have any further problems u can do wat i did download Automatix
it'll come up wit a list with usefull programs for linux like, flash player, java runtime enviroment, PDF reader, linux msn messenger stuuf's like that it'z a very usefull program [AutoMatix]("http://www.getautomatix.com")

---

### Post by ktat on 2009-02-05
I was having pretty much the same problem, I also tried installing opera 9.63. Java games were working but it didn't matter what browser I was using, runescape wouldn't.

I am a total newbie, so I figure this must be just about the simplest solution for Runescape not working in Firefox browser using Ubuntu 8.04.

[LIST=1][*]go to Add/Remove under the applications menu[*]show all available applications and type "venkman extension" into search box[*]upload venkman extension[*]start up firefox and go to runescape page where java is not working[*]the extension will start up and ask for a place to save temp files, leave it on default (ie /tmp)[*]get back to gaming :)
[/LIST]
I still have a small problem though, sound is a bit sketchy - not sure why.  I have amd athlon processor and 512mb graphic card with 2G of ram so I don't think it's a lack of decent hardware.

---

