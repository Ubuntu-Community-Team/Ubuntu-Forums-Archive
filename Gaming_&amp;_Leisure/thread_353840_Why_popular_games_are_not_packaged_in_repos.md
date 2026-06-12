---
title: "Why popular games are not packaged/ in repos?"
date: 2007-02-05
forum: Gaming &amp; Leisure
---

### Post by geokok1981 on 2007-02-05
I know that gaming in linux has still some way to go. However, there are some good games that seem to be popular like enemy territory, true combat elite, sauerbraten etc. (these are just examples)

Does anybody else thinks it is weird that although the good titles are few nobody seems to be making packages of them or including them to the repos? I mean it would be nice to have a clean easy install instead of running a .sh script most of times. I have friends you prefer using  an .exe for windows for game A rather than reading how to install game A in its linux version because it is not so straightforward procces without a package for them. 

What is your opinion on that?

---

### Post by Sqwishy on 2007-02-05
Yeah sometimes they don't put it up because the things arn't open source, so they can't be put into deb files or something. But for wesnoth 1.21 i had to compile it myself because it wasn't in the main repo's! And it's says it's stable on the site! Wtf!?

---

### Post by Mateo on 2007-03-27
I don't get it either.  there are some good games in the repos, but a lot that's not.  the thing about installing it manually is, how do you uninstall?  how do you uninstall .run files?  so if I get wolfenstein and don't like it, then what?  just screwed?

---

### Post by Perfect Storm on 2007-03-27
> **Sqwishy said:**
> Yeah sometimes they don't put it up because the things arn't open source, so they can't be put into deb files or something. But for wesnoth 1.21 i had to compile it myself because it wasn't in the main repo's! And it's says it's stable on the site! Wtf!?


Because the repo only gets security updates etc. It's nothing, it have always been like this. It might get lucky to reach feisty?

> I know that gaming in linux has still some way to go. However, there are some good games that seem to be popular like enemy territory, true combat elite, sauerbraten etc. (these are just examples)

Does anybody else thinks it is weird that although the good titles are few nobody seems to be making packages of them or including them to the repos? I mean it would be nice to have a clean easy install instead of running a .sh script most of times. I have friends you prefer using an .exe for windows for game A rather than reading how to install game A in its linux version because it is not so straightforward procces without a package for them.

What is your opinion on that?

As Sqwishy said, They aren't GPL or it havn't been tested/build a package for Ubuntu to reach into the repo.

> **Mateo said:**
> I don't get it either.  there are some good games in the repos, but a lot that's not.  the thing about installing it manually is, how do you uninstall?  how do you uninstall .run files?  so if I get wolfenstein and don't like it, then what?  just screwed?

Check for an uninstaller script where the game is installed, if it doesn't have one simple delete that game and its /bin file.

---

### Post by Mateo on 2007-03-27
but in linux files get spread everywhere.  how would i know where all of the files are to delete them?

---

### Post by Perfect Storm on 2007-03-27
A good command(s) is

```
whereis <name>
locate <name>
```

---

### Post by Mateo on 2007-03-27
how do I know the name of every file?

---

### Post by Perfect Storm on 2007-03-27
You don't have to.
Lets say it's battle for wesnoth
you just whereis wesnoth
and/or locate wesnoth

---

### Post by eentonig on 2007-03-27
files normally don't get installed unpredictably anywhere and are usually contained in folders which should reference the 'package' for which they contain files.

---

### Post by Mateo on 2007-03-27
'normally' isn't good enough to me.  I don't want a single file, a icon or man file or anything, on my system unless I have that piece of software installed.

---

### Post by Lord Illidan on 2007-03-27
> **Mateo said:**
> 'normally' isn't good enough to me.  I don't want a single file, a icon or man file or anything, on my system unless I have that piece of software installed.

Again, locate **will** definitely hunt down those files, and calm down man, it's not like 1 icon misplaced is going to affect you.

---

### Post by Mateo on 2007-03-27
i am calm.  1 misplaced icon takes up more space than 0 misplaced icons. I don't like wasted space.  i'm not as confident in using search as you all seem to be.  I don't believe that every last file installed either uses the game's name in its filename or is located in a folder named after the game.

---

### Post by ceeg on 2007-03-28
> **Mateo said:**
> i am calm.  1 misplaced icon takes up more space than 0 misplaced icons. I don't like wasted space.  i'm not as confident in using search as you all seem to be.  I don't believe that every last file installed either uses the game's name in its filename or is located in a folder named after the game.

That is usually the case, actually. (Specifically for this purpose, I've always believed).

Say you are installing wesnoth:

/usr/bin/wesnoth
/usr/local/games/wesnoth
/usr/share/docs/wesnoth

etc. That's just how makefiles are made.

---

### Post by Keffin on 2007-03-28
> **Mateo said:**
> i am calm.  1 misplaced icon takes up more space than 0 misplaced icons. I don't like wasted space.  i'm not as confident in using search as you all seem to be.  I don't believe that every last file installed either uses the game's name in its filename or is located in a folder named after the game.

Having packages in the repos doesn't actually fix this anyway. apt-get remove X will only remove the files that were created when you apt-get installed X. It's pretty hard to find a program that doesn't create files at runtime e.g. in /etc or ~/ (hidden directories for config and game saves) and so on.

At the end of the day if you just remove the main directory where things were installed then you'll be left with all of a couple of kb max of settings/icons. Apt will be able to remove a little more than just the main directory, using locate will probably help you easily remove more than apt - do you now suddenly care that apt isn't doing things perfectly?

It is a (very) hard problem to solve with the directory structure common to most linux distributions. One way of avoiding this issue is the common way of doing things in Mac OS (I am led to believe) and GoboLinux. The GoboLinux web site describes their method ([http://www.gobolinux.org/?page=at_a_glance):](http://www.gobolinux.org/?page=at_a_glance):)

> GoboLinux is a modular Linux distribution: it organizes the programs in your system in a new, logical way. Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.

I've gone somewhat off topic there wrt to making things work on ubuntu, but I thought it was interesting :?.

---

### Post by Lord Illidan on 2007-03-28
> **Keffin said:**
> Having packages in the repos doesn't actually fix this anyway. apt-get remove X will only remove the files that were created when you apt-get installed X. It's pretty hard to find a program that doesn't create files at runtime e.g. in /etc or ~/ (hidden directories for config and game saves) and so on.

At the end of the day if you just remove the main directory where things were installed then you'll be left with all of a couple of kb max of settings/icons. Apt will be able to remove a little more than just the main directory, using locate will probably help you easily remove more than apt - do you now suddenly care that apt isn't doing things perfectly?

It is a (very) hard problem to solve with the directory structure common to most linux distributions. One way of avoiding this issue is the common way of doing things in Mac OS (I am led to believe) and GoboLinux. The GoboLinux web site describes their method ([http://www.gobolinux.org/?page=at_a_glance):]("http://www.gobolinux.org/?page=at_a_glance%29:")



I've gone somewhat off topic there wrt to making things work on ubuntu, but I thought it was interesting :?.

Also sudo apt-get remove --purge X will remove config files as well.

---

### Post by Famicommie on 2007-03-28
From what I've read, aptitute does a cleanener job of removing all libraries and config files.

[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

---

### Post by Mateo on 2007-03-28
> **Keffin said:**
> Having packages in the repos doesn't actually fix this anyway. apt-get remove X will only remove the files that were created when you apt-get installed X. It's pretty hard to find a program that doesn't create files at runtime e.g. in /etc or ~/ (hidden directories for config and game saves) and so on.

At the end of the day if you just remove the main directory where things were installed then you'll be left with all of a couple of kb max of settings/icons. Apt will be able to remove a little more than just the main directory, using locate will probably help you easily remove more than apt - do you now suddenly care that apt isn't doing things perfectly?

It is a (very) hard problem to solve with the directory structure common to most linux distributions. One way of avoiding this issue is the common way of doing things in Mac OS (I am led to believe) and GoboLinux. The GoboLinux web site describes their method ([http://www.gobolinux.org/?page=at_a_glance):](http://www.gobolinux.org/?page=at_a_glance):)



I've gone somewhat off topic there wrt to making things work on ubuntu, but I thought it was interesting :?.

no, I do not like that apt-get doesn't always get everything, but that's the best I can do.  Synaptic complete removal gets most everything.  I can handle deleting the ~ stuff myself.  I do not like a single file on my computer that I don't want there.  If you let stuff like this go, eventually you have to reformat your computer and I never want to do that.  I don't like messes.

---

### Post by houstonbofh on 2007-03-29
If you are really worried, just 'more' the install script.  That will tell you where EVERYTHING was placed.  And that is actually more than synaptic will tell you.

---

