---
title: "Where do the apps go?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by elpuerco on 2006-09-08
I installed a load of apps last night using Adept and all went fine.

But when I look at the K menu I see some of the apps I installed, but not others?

For example I installed a German-English dictionary but cannot see how to start it?  :confused:

---

### Post by pyros on 2006-09-08
Yeah, I've run into that with some applications in ubuntu. The best thing I can tell you to do is find the name of the executeable file and create a  launcher for it. If you look in the "properties" for the .deb packages it should have a list of files installed. look for the name of the files it puts in a "bin" directory, that should be the one.

---

### Post by hraposo on 2006-09-08
try this if is a .deb pacckage:
apt-cache search adept --full|less

---

### Post by elpuerco on 2006-09-08
:) Thnx, I will try this and let you know what happens :)

---

### Post by elpuerco on 2006-09-08
OK I am completely discombobulated!!

I have installed dictd German-English Translation Dictionary for dictd

I also have dictd installed

Looking at Adept Details -> Installed Files I see lines and lines of directories and sub directories but no files?

/etc plus subdirectories
/usr plus subdirectories
/var plus subdirectories

I dont know how to id the required executable?

Help please....:confused:

---

### Post by skymt on 2006-09-08
dictd runs in the background. You need a client for it, like kdict.

---

### Post by elpuerco on 2006-09-08
OK so I still have two problems...

1. How would I know that if I chose to install a program that I need another to make it work?  Does not Adept install all required libs/progs etc?

2. Again I have installed Kdict but once again no entry on the K menu?  I lookup the details in Adept and again a long list of directories but no file names.

Am I missing something big here?  How do you installl a program and find out where it went so you can create a launcher for it?

Also why does the instraller simply place an entry on the K menu?

Sorry for the barrage of questions.....:confused:

---

### Post by skymt on 2006-09-08
1. Yes, Adept installs everything a program needs to run. However, dictd can be usefully installed without a client (so clients can connect over a network), and kdict can be usefully installed without dictd (to connect to a dictd over a network). Often, when a package works better if another is also installed, it will "Recommend" or "Suggest" it. I don't know how Adept shows these, I use aptitude.

2. You need to edit the K menu. Add an entry that launches the command "kdict".

Many packages don't come with menu entries, because nobody's added them. It's that simple: laziness.

Often, if a package contains a program, the program and package have the same name. For example, dictd contains the dictd command, and kdict contains (or should, I don't have it installed) the kdict command.

The (very small) rest of the time, you have to look around. I really doubt that the kdict package has only directories. Look in the kdict package details in Adept, for a file in /usr/bin. That's where most programs end up.

---

### Post by pyros on 2006-09-08
> **elpuerco said:**
> Am I missing something big here?  How do you installl a program and find out where it went so you can create a launcher for it?

Generally you don't have to know where it went, just the name of the binary file. For example: for kdict, just create a launcher for "kdict" not "/usr/bin/kdict"

---

### Post by nrwilk on 2006-09-08
I find the debian menu helpful.

This is a menu which will appear in your kmenu.  It will display anything that has been installed from a repository, or from a .deb package.

To get it, just issue this command:
```
sudo aptitude install menu
```

The menu divides software into categories so that stuff is easy to find.


**Also**, I find that when I install software it isn't always added to the kmenu right away.  I fix it each time I install software by doing this:

1) Right-click the kmenu and select "Menu Editor."
2) When the menu Editor opens, click the floppy disk image to save the menu configuration.  This should be the first icon on the toolbar of the Menu Editor.  It doesn't matter that you haven't changed anything.
3) Close the Menu Editor.
4) Check to see if the kmenu now displays your new software.

:D 

nrwilk

---

### Post by elpuerco on 2006-09-09
Kool :D 

Thanks for the info folks...

I did not know about how to edit the Kmenu, I do now :D 

I can now see kdict, just need to see about how to use it thnks.

I installed the debian menu and it was not there on the kmenu :confused: 

I came back here to ask why and saw the post re simply edit kenu and save and all appear, hey presto.....debian menu appeared.

:D  :D  excellent :D

---

