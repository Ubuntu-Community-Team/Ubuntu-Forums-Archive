---
title: "Trouble with GNOMEDo Dock in KDE"
date: 2009-05-13
forum: Desktop Environments
---

### Post by SG2 on 2009-05-13
I hope this is the right category in which to ask this question.

I'm new to Linux, having just installed Kubuntu on my laptop a week ago (I'd previously tested Fedora on my thumbdrive, but never extensively used Linux before now).  I'm getting the hang of it pretty quickly, because everything that isn't straightforward I've found information for online, much of which I found on this forum...

But the one thing I feel is missing from my perfect desktop environment is a program dock.  I use XP normally, and I love Stardock's ObjectDock software, so I went searching for a similar dock experience available for KDE.  I tried Cairo Dock and I didn't like it, but I heard great things about GNOMEDo and that it would, despite the name, run on KDE.

I'm running KDE4; the Kubuntu I just installed was the newly-released Jaunty Jackelope (it was reading up on new releases that got me to decide to test Linux out on a full partition; initially I was set to try the Windows 7 RC).  I've got GNOMEDo running, but it won't let me change the theme to anything but the default (the dropdown box is grayed out).  I'm assuming this has something to do with a KDE bug, but I've seen screenshots of it running on Kubuntu, so I know I'm doing something wrong.

So can someone tell me what to do to change my theme to Docky?  GNOMEDo seems to be working well otherwise, but the main reason I sought it out in the first place was for the dock, so it'd be a real shame not to be able to use it.

---

### Post by SG2 on 2009-05-14
I just noticed, the reason I can't change themes is because, according to GNOMEDo,

"Your display is not properly configured for theme and animation support.  To use these features, you must enable composing."

Sorry for being a total Linux n00b, but what is composing, and how do I enable it?

---

### Post by benerivo on 2009-05-14
I think it said compositing, which is window management that adds 'desktop effects' such as translucency, shadows, wobbly windows, etc. The most popular one is compiz, but in kde4 they have there own inbuilt compositing effects. You could try turning on the kde4 desktop effects in the 'system settings' section, and try the gnome-do options again.

---

### Post by SG2 on 2009-05-14
That solved the problem.  In the Desktop settings I was able to change compositing style to 'XRender' and now I'm able to change the themes.  

Thank you for the help!!

---

