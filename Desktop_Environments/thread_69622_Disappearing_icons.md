---
title: "Disappearing icons"
date: 2005-09-27
forum: Desktop Environments
---

### Post by Old *ix Geek on 2005-09-27
I'm having a bit of an odd problem and I really don't have a clue as to why this is happening.

In my taskbar, I've added several applets/toys/applications.  One suddenly disappeared altogether--and the worst part is I can't find it to add it back!--and the other disappears occasionally.  The one I can't find was a volume control, very small and simple with basically just one slider to raise the volume from 0-100%.  I have no idea where/what that was, but I can't find it anywhere now. The other one, that occasionally disappears, is the Tea Cooker toy.  Sometimes when I log back in it's gone.

Finally, I've also lost the System | Settings | Sound & Multimedia | Sound System icon, and don't know how to add it back.

---

### Post by mlomker on 2005-09-27
Look in the Control Panel under KDE Components, Session Manager.  Do you have it configured to 'restore manually saved session' or something else?  I prefer that setting because then it isn't going to use whatever I had opened at shutdown.

The volume control that I use is **kmix**.  You can just type that onto the Run line, even if the icon isn't in your menus.

>  Sound System icon,

Do you mean that it is missing from Kcontrol altogether?  I suppose you could force a reinstall of the **kdemultimedia** package but that'll install quite a few pieces.  Maybe try reinstalling **kmix** first?

---

### Post by Old *ix Geek on 2005-09-27
> The volume control that I use is **kmix**.  You can just type that onto the Run line, even if the icon isn't in your menus.Thanks!  That's what I had been using.
> Sound system icon,

Do you mean that it is missing from Kcontrol altogether?  I suppose you could force a reinstall of the **kdemultimedia** package but that'll install quite a few pieces.  Maybe try reinstalling **kmix** first?Yes, it's missing altogether.  Instead of four items under System | Settings | Sound & Multimedia, there are only three because "Sound System" is missing.  I don't know where it went, but it's gone!  I tried reinstalling the kdemultimedia package but "Sound System" is still missing.  This being Linux, I KNOW there has to be a way to manually add it back, but since I don't know what's behind it, I have no idea what to do.

---

### Post by mlomker on 2005-09-27
>  This being Linux, I KNOW there has to be a way to manually add it back, but since I don't know what's behind it, I have no idea what to do.

I spent some time searching my filesystem but I couldn't find anything obvious.

---

