---
title: "How do i make rythembox do this?"
date: 2006-03-08
forum: Desktop Environments
---

### Post by StueyB on 2006-03-08
Hi peeps,

I guess for you ubuntu Gurus its an easy question, but one of the features I miss from XP is the ability to right click on a folder and have it play the folder contents. Is there any way to do this in Ubuntu because its a faf otherwise.

---

### Post by JELaVallee on 2006-03-08
I think this could be accomplished with a Nautilus actions script, if someone hasn't already done it.

Nautilus scripts allow you to define customized launch actions and other neat functionality in Nautilus.  [Here's a thread]("http://www.ubuntuforums.org/showthread.php?t=91377") with info on such and a bunch of scripts others have created.  I'll dig around and see if what you're looking for exists or if I can throw it together (I too would enjoy such a feature).

cheers,
Etienne

---

### Post by JELaVallee on 2006-03-08
Okay,

This thread:
[http://www.ubuntuforums.org/showpost.php?p=567707&postcount=22]("http://www.ubuntuforums.org/showpost.php?p=567707&postcount=22")

Explains how to use the Nautilus Actions tool to create an script to do what you want using the Totem media player.  It won't work if you substitue in rhythmbox for the application name because rhythmbox doesn't appear to be able to open specific files from either the commandline or from the app itself.  Which makes sense since Rhythmbox is really positioned as just a media library-oriented player/organizer.

I've tried the totem script and it works, but totem isn't ideal for me... so I substituted xmms in (it's a media player very similar to WinAmp in functionality and feel) and that works great, you can even right-click on the xmms player and select "View Playlist" to see all the files you've loaded.

Let me know if you need any help...

cheers,
Etienne

---

