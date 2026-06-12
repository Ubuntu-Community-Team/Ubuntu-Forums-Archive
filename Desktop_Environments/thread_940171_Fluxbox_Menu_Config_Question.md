---
title: "Fluxbox Menu Config Question"
date: 2008-10-06
forum: Desktop Environments
---

### Post by voltaire99 on 2008-10-06
Hi all,

I have looked all over the place for this and tried a million different things.  I would like to have a single menu entry that will open several config text files as tabs in one instance of geany.  I have gotten it to work this way:

(Fluxbox Config) {geany /home/xx/.fluxbox/init & geany /home/xx/.fluxbox/menu & geany /etc/X11/fluxbox/fluxbox-menu}

However, if I use this before opening geany for something else it will not open the tabs properly.  I need a sleep, or wait between the commands to make it work properly.  Can anyone help with this?

---

### Post by jay019 on 2008-10-06
Maybe make a geany project with all the files you want to open and then open that?
Just a thought, let me know if it works.

---

### Post by voltaire99 on 2008-10-06
Couldn't make the project work either, because, despite trying, I could not find a command to open the project from outside of geany.

---

### Post by voltaire99 on 2008-10-06
Triying:
[exec] (Fluxbox Config) {geany /home/xx/.fluxbox/init & sleep 10 & geany /home/xx/.fluxbox/menu & geany /etc/X11/fluxbox/fluxbox-menu}

---

### Post by jay019 on 2008-10-07
Ah, your right. It wont be available until version 0.15...
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/7fec6e8f034a458e](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/7fec6e8f034a458e)

Oh well, I tried ;)

---

### Post by voltaire99 on 2008-10-07
Jay019-It was a good idea, thanks for it.  

Adding sleep didn't help, the first time I run the command it opens seperate instances of geany.  It is made even more frustrating because at some point I was using a version of antix that did this perfectly.  I have since thrown that antix cd out.  I have burned two antix releases trying to find that particular setup (I thought it was 7.2), but have been unable to hit on the right one.

---

### Post by anticapitalista on 2008-10-07
[exec] (Fluxbox Config) {geany ~/.fluxbox/menu ~/.fluxbox/keys ~/.fluxbox/init ~/.fluxbox/startup ~/.fluxbox/apps}

---

### Post by voltaire99 on 2008-10-07
Thanks for that anticapitalista.  It looks like I basically had the right idea.

Also wanted to say that antiX is awesome; lightwieght, beautiful, very user friendly, and always getting better, it is definitely a favorite.

---

