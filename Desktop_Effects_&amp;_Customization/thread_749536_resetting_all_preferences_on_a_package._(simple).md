---
title: "resetting all preferences on a package. (simple)"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by jesusfreak107 on 2008-04-08
Okay, I am a linux obsessed person, and an aspiring IT guy, yet my experience is still limited, and I do not know a lot of the basic commands.  What I do know, I make sure I know *well*, but I do not know much.  Could someone please instruct me on how to reset a package.  as in, when I reinstall Compiz, all my preferences are there from last time.  How do I reinstall a package, and not have this happen.  If I have used Compiz, and customized it *heavily*, and decide that I want to start over completely, what do I do?  Thanks in advance!
Oh, and I am looking for something easier than completely removing the package, and re-downloading it.
:guitar:

---

### Post by .nedberg on 2008-04-08
Most programs have a hidden folder with settings in your home directory.

I don't use compiz, but I would guess it is /home/<username>/.compiz

---

### Post by FuturePilot on 2008-04-08
It's actually in /home/<USER>/.config/compiz

But the thing is Compiz by default uses Gconf to store settings so resetting everything can be a bit of a pain. Luckily in CompizConfig there's an option under Preferences down in the bottom left corner that will let you reset everything to the defaults with a click of a button. ;)
But most of the time removing the . dot folder for the program will reset all the settings.

---

