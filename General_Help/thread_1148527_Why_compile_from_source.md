---
title: "Why compile from source?"
date: 2009-05-04
forum: General Help
---

### Post by Vyder on 2009-05-04
Why does it even exist? Why can't everything just be .deb files to nicely double-click and install?

---

### Post by 3Miro on 2009-05-04
IF everything is .deb, then it is fixed. You cannot change a .deb file. This is one of the main problems on windows, there is no source, so if there is a new version of windows, everything old stops working and there is nothing to be done about it (look at what happened with vista). There is a new version of Ubuntu every 6 months and if something breaks form the old one, the developers can just look at the code and fix it and recompile it.

Most stuff actually exists in .deb format. What are you trying to compile? If someone out there has made a program, then it is up to them to make a .deb. Also, if you are building something from source, then you can see what is inside (unlike closed source, when you really don't know what you are getting). That is why spyware does not exist in the open source world.

---

### Post by binbash on 2009-05-04
Because you may want to add additional features like amr support for mplayer.Also it will be faster than deb file if you can compile it right.

---

### Post by benj1 on 2009-05-04
first, not every distro uses .debs eg rpms, some such as slackware by default use source, rather than compiled binaries.
second though related to the first, alot of open source/linux stuff is written by a single person for no other reason but for the fun/challenge of it and making 15 different packages wasn't why they developed it, they aren't getting paid for it after all. 
third gpl programs have to make the source available anyway so why not make it so people can easily compile and install themselves, may even encourage people to take a look at the source and submit patches/improvements.

---

### Post by Vyder on 2009-05-04
Makes sense.

I am just frustrated cause I finally figured out how to compile and install something (btnx) then I found I needed some dependencies, and that went on and and on 5times.

I guess eventually when I get to a point where source code makes sense, I'll appreciate it too...till then...ugh

---

### Post by HydroTech on 2009-05-04
Dude! I know what you mean Vyder. Source code looks overwhelming when I look at it all at once but I understand it more when I look at it one line at a time. And if you know how to write in that certain computer language for that program, it's pure power for you.LOL

---

### Post by benj1 on 2009-05-04
its known as dependency hell, thats why we have package managers :)

---

### Post by HydroTech on 2009-05-04
> **benj1 said:**
> its known as dependency hell, thats why we have package managers :)

Yes, I'd say "if you just want to run the program, ignore source and go for package manager. And(for the most part) if you have to compile it yourself, don't use it.(unless you want to edit stuff yourself)
:guitar:

---

### Post by Vyder on 2009-05-05
so far I only know Java and webpage coding properly, and a bit of Perl and C. Trying to learn shell scripting, looks like fun. =)

---

### Post by andrew.46 on 2009-05-07
Hi benji,

> **benj1 said:**
> first, not every distro uses .debs eg rpms, some such as slackware by default use source, rather than compiled binaries.

A minor quibble: Slackware actually uses binary packages with a .tgz suffix *by default* and in fact there are many collections of *3rd party* packages in this format. However it is true that die-hard Slackers would normally avoid these 3rd party packages and use the type of 'wrapper' scripts + source found in such places as slackbuilds.org or better still write their own scripts.

All the best,

Andrew

---

