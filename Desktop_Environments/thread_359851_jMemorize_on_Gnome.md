---
title: "jMemorize on Gnome"
date: 2007-02-12
forum: Desktop Environments
---

### Post by teabeartom on 2007-02-12
I downloaded the .jar file for jMemorize (jmemorize.org) and ran it using the command: java -jar jMemorize---------.jar

The program loaded, but the interface is really bad.  In the terminal, it brought up an error message saying that it could not find the "clearlooks" engine.  The category drop down bar is only about two pixels wide, so I can't see my categories either.  Has anyone else had this problem?

I remember I used jMemorize with KDE a few months back, and it came up fine.  Thanks for your help.

---

### Post by dinin_1985 on 2007-03-07
I am having this problem. And having other problems too. My categories are not save, as it worked in the winxp version, and I can't find a menu shortcut or create a launcher or something alike. 
It's very frustrating to not find my categories when I reopen that thing... besides the problem with the categories drop down menu.......
anyway, YOU solved my problem.......: as I mean to use jMemorize a lot I'll change to Kubuntu if I can't solve the problem until next week.

---

### Post by teabeartom on 2007-03-26
OK,
I emailed the main developer of jMemorize and he said that there is a bug with java that has been reported here:

    [https://launchpad.net/ubuntu/+source/ubuntulooks/+bug/34688](https://launchpad.net/ubuntu/+source/ubuntulooks/+bug/34688)

He said that if we upgrade to java 6 beta, then it should work fine.  I believe it is a bug with how java is reading the GTK2 theme in certain java programs so that it badly mishandles it, and that may be why it uses a generic widget theme when run under KDE...

---

### Post by thinkbuddha on 2007-05-30
Just a - belated - comment on linking to the menu or to the panel. I'm using KDE, and it's easy to create a launch button. Just right click the panel, choose "Add Application to Panel", choose "Add Non-KDE Application", then in the dialogue box that opens up, choose an icon, give your button a title, and under "Executable" link to the file as follows (replacing /path/to/file/ with your path, of course - and I renamed the jMemorize file to jMemorize.jar, but you get the idea)

> java -jar /path/to/file/jMemorize.jar

That should give you a nice, quick button to start the app in KDE.

Will

---

