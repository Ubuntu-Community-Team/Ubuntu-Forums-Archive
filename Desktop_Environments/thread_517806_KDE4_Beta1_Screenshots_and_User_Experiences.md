---
title: "KDE4 Beta1: Screenshots and User Experiences"
date: 2007-08-05
forum: Desktop Environments
---

### Post by smartboyathome on 2007-08-05
I have taken some screenshots of KDE4 Beta1, and am going to document my exploration into KDE4 Beta1 (which I know is still not done, and will have many bugs; this trip should not be taken by anyone who hates to get bugs!). So, let us dive into a trip filled with the unexpected (for me, at least)!

Day 1 (installation + first thoughts):
KDE4 has been brewing for a while, and this is just a tip of the iceberg compared to what is to come. When I first booted up, I was greeted by a nice picture of the KDE development team (I am sad to say I could not get a screenshot of that). After, I was taken to a rather snazy looking desktop that is quite different from what I expected. I found the combo of gray+blue soothing, but not at all exciting! Just what I needed to calm my nerves. ;)
I then explored one of the main attractions: the newly revamped Dolphin File Manager. It was not what I expected with the sort of functionality I got from it. Being a GNOME user, I didn't like Konqueror very much, so seeing dolphin gave me something familiar. I came across a setting which gave me a functionality quite like the Mac OSX file browser (sadly, I cannot repeat what I found, as I cannot find the setting). I also noticed the new look of the windows, quite appropriate! That is all for tonight, I will update this thread with more tomarrow!

For now, the screenshots are attached.

---

### Post by LuisAugusto on 2007-08-05
Before people get confuse:

-That isn't Oxygen Theme.
-There are around 15 plasmoid, not just one.
-Kicker won't be on KDE 4.0.

And, to the author:

-Dolphin is amazing, isn't it :)?
-You should test Okular, quite impresive too.
-Amarok is too incomplete, but you still can give it a shoot.
-Konqueror has a new GUI arrange, it looks similar to epiphany and it's using WebKit (aka Safari Engine, which is based on KHTML [aka Konqueror web-browsing engine]), it's damn fast.

---

### Post by GeneralZod on 2007-08-05
> **LuisAugusto said:**
> 
-Konqueror has a new GUI arrange, it looks similar to epiphany and it's using WebKit (aka Safari Engine, which is based on KHTML [aka Konqueror web-browsing engine]), it's damn fast.

Actually, the future of khtml is still not 100% decided, so current Konqueror is definitely still using khtml.

Its future replacement by WebKit is looking very likely, though.

---

### Post by happysmileman on 2007-08-05
> **LuisAugusto said:**
> 
-That isn't Oxygen Theme.


Yes but is the oxygen theme that I see in "kcmshell styles" almost finished, looks good, but can definitely be improved?

> **LuisAugusto said:**
> 
-There are around 15 plasmoid, not just one.


Where can I get the rest to test? Can I? I'd like to see how my computer copes with a few different plasmoids running...

Does anyone have any way I can get more? I don't mind compiling or anything.

> **LuisAugusto said:**
> 
-Dolphin is amazing, isn't it ?


I agree, it's incredible, I'm assuming it's almost done? I can't think of anything else to include, and unlike pretty much everything else I've tested (not much admittedly) it didn't crash once

---

### Post by Erunno on 2007-08-05
> **happysmileman said:**
> Yes but is the oxygen theme that I see in "kcmshell styles" almost finished, looks good, but can definitely be improved?

The widget style is disabled for the time being while being rewritten. From the look of it it seems that the animations are still not working. I'm also sure that they wlll tweak it in the future depending on user feedback.


> Where can I get the rest to test? Can I? I'd like to see how my computer copes with a few different plasmoids running...

Does anyone have any way I can get more? I don't mind compiling or anything.

They can be found in playground on the svn server. I don't know if Kubuntu packaged them as well though.

> I agree, it's incredible, I'm assuming it's almost done? I can't think of anything else to include, and unlike pretty much everything else I've tested (not much admittedly) it didn't crash once

It's seems to be pretty complete for the 4.0 release for the time being but there are still features in the pipeline for subsequent releases. Most prominent I can think of at the top of my head is integration with the Nepomuk framework. There's already a prototype developed by Mandriva but it hasn't been merged yet / is deactivated.

---

### Post by happysmileman on 2007-08-05
> **Erunno said:**
> They can be found in playground on the svn server. I don't know if Kubuntu packaged them as well though.

Have you gotten them to build? I've downloaded them, but when I cd to the folders for them I don't really know what to do...

I've tried to use "cmake" but that gives me the error that I need "qmake", and when i try to install qmake it tells me to install "kde4libs-data", which won't install, presumably because it's version 3.80 instead of 3.92?

Anyone know how to do this?

---

### Post by happysmileman on 2007-08-06
Bumpety

---

### Post by Darkhack on 2007-08-06
One question I have about KDE 4 is the theming engine.  Has it been improved at all?  In 3.5 it is such a pain to install new themes because you have to do every little thing manually.  Copy all the files to the proper folders spread out on the system and then alter config files and all this crazy stuff, where as in GNOME, you just select the tarball and you're good to go.

---

### Post by smartboyathome on 2007-08-06
For now, you still have to copy the config files and do all that. This is probably going to change in the near future, but for now, this is how themes are handled.

---

