---
title: "changing window manager"
date: 2005-07-06
forum: Desktop Environments
---

### Post by pear-i on 2005-07-06
hey i searched around the forums but couldn't really find anything that worked so here goes..

basically what i'm trying to do is to change the default WindowManager from metacity (default with ubuntu) to Kahakai ([http://kahakai.sourceforge.net/index.php](http://kahakai.sourceforge.net/index.php)) 
i installed the .deb file and everything works fine... except i have no way of starting X with it -- i uninstalled metacity (since i'm planning to use kahakai full time) and right now after GDM starts it pauses at the window manager and throws open an xterminal asking me to run the window manager, i type in kahaki and it runs... i get the different menus -- then everything reverts back to gnome 

so i was just wondering
if you guys might have an idea on how i might implement it the <b> proper way </b> say setting it to default for gdm... and so the interface actually stays after gnome is incorporated.

thanks

(note - i've tried changing the xinitrc... but don't think that worked at all.

---

### Post by frodon on 2005-07-06
Have you try to add a command in System>Preferences>Session ? Maybe if you add "kahakai --replace " it will use kahakai each time you start a session.
It's just an idea, sorry if it doen't fit to your need.

---

### Post by wylfing on 2005-07-06
First, some lighthearted chastisement: you couldn't have searched too hard!
[http://www.ubuntuforums.org/showthread.php?t=40138&highlight=changing+window+manager](http://www.ubuntuforums.org/showthread.php?t=40138&highlight=changing+window+manager)

Anyway, are you sure you know what you're asking for? Gnome runs on top of a window manager (by default, Metacity). So changing WMs does not replace Gnome -- the windowing behavior will just be a little different while you're in Gnome. It is also possible to run a WM without loading Gnome, and this is what I assume you're trying to do. In that case, log out, and click on Sessions. You should be able to choose the WM as a session, which will run it *sans* Gnome.

HTH

---

### Post by pear-i on 2005-07-06
[QUOTE=wylfing]First, some lighthearted chastisement: you couldn't have searched too hard!
[http://www.ubuntuforums.org/showthread.php?t=40138&highlight=changing+window+manager](http://www.ubuntuforums.org/showthread.php?t=40138&highlight=changing+window+manager)

Anyway, are you sure you know what you're asking for? Gnome runs on top of a window manager (by default, Metacity). So changing WMs does not replace Gnome -- the windowing behavior will just be a little different while you're in Gnome. It is also possible to run a WM without loading Gnome, and this is what I assume you're trying to do. In that case, log out, and click on Sessions. You should be able to choose the WM as a session, which will run it *sans* Gnome.

HTH[/QUOTE]
 frodon - i tried to add the new sessions but it seems to just hang at the loading windows manager screen.. and after a really lon time it loads.. 

wylfing --  i tried the kahakai --replace and it just seems to be an unknown option, not to mention can't choose WM  as a session... it just gives me teh default... thats why its sorta boggling me right now :\

---

### Post by wylfing on 2005-07-06
Doh that's not the thread I intended to link to  :neutral: . It was supposed to be this one:
[http://www.ubuntuforums.org/showthread.php?t=15193&highlight=changing+window+manager](http://www.ubuntuforums.org/showthread.php?t=15193&highlight=changing+window+manager)

What I was after was using update-alternatives. I've used that to switch WMs. But since it sounds like what you're really after is a non-Gnome session that's kind of a dead end for you.

It sounds like the Kahakai packages aren't doing what they're supposed to do. Try reinstalling metacity and then reinstalling kahakai, making sure you have the latest kahakai debs. I noticed on the project page that there's some, er, looseness about where the right debs are. Kahakai is also an immature project and it's very possible things just won't work well until it gets some more miles under its belt.

After reinstalling, If Kahakai doesn't show up as a session option in GDM, then the packages aren't working. At that point, if you are still committed to using Kahakai, I'd suggest downloading the tarball and compiling from source. That, or try contacting the package maintainer and asking his advice.

---

### Post by frodon on 2005-07-06
I install kahakai with the deb file .... and it not seems to work well, indeed kahakai --configure don't exist and there isn't an option in the session menu in login screen, strange ... I will try the sources. But if someone have kahakai running thanks to post here a way to run it.
I never read anything before on kahakai but it looks nice when you see the screenshots on the website, I'm curious to test it.

---

