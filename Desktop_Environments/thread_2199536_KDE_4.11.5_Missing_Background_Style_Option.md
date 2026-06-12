---
title: "KDE 4.11.5 Missing Background Style Option"
date: 2014-01-14
forum: Desktop Environments
---

### Post by mpmistr on 2014-01-14
Hey I am running Kubuntu 13.10 and just received the upgrade for 4.11.5. I noticed after the upgrade under the Window Decoration options for Oxygen that under the Fine Tuning and Window Override options, the ability to select Background Style is gone.. it allowed you to change the title bar from "follow hint style", "radial gradient", and "solid color".

I kind of liked this feature since it allows you to make some applications, like Chrome look better integrated into KDE. Either way, my title bars use radial gradient now and I cannot change it or override any windows since it was removed.

Has anyone else experienced this?

---

### Post by marco-parillo on 2014-01-14
I did not know that option even existed, but I can confirm that it has been removed.
My installation of Kubuntu 13.10 is still at 4.11.3, and it has the option you describe, and my installation of 14.04 (Alpha-1 with all updates applied) on Platform Version 4.12.0 lacks it.
I will try to remember to update my post when I receive updates to 13.10.

---

### Post by mpmistr on 2014-01-14
I have a laptop running KDE running 13.10 and it's still there. It was there before I did the update to 4.11.5 last night. My laptop has not received the 4.11.5 update yet.

That is kind of crazy, I wonder why they would remove it?

---

### Post by marco-parillo on 2014-01-14
Sometimes if you file an upstream bug at bugs.kde.org you get some good information, or a pointer to a maling list where it was discussed.

---

### Post by marco-parillo on 2014-01-16
Bug opened:
[https://bugs.kde.org/show_bug.cgi?id=330035](https://bugs.kde.org/show_bug.cgi?id=330035)
Assigned to Oxygen > Windows Decoration.

---

### Post by marco-parillo on 2014-01-17
From the bug report:

The option has actually been replaced by  [Common] UseBackgroundGradient=true  (or false)  in $HOME/.kde(4)/share/config/oxygenrc

---

### Post by mpmistr on 2014-01-17
Thank you very much! It appears the UI element is just missing right now.

---

### Post by marco-parillo on 2014-01-27
In the [bug report]("https://bugs.kde.org/show_bug.cgi?id=330035"), it looks as if the fix has been committed:
[COLOR=#2E3436][FONT=Open Sans]Git commit 05442b10ca9c9464d8153608e18bc065297a239e by Hugo Pereira Da Costa.Committed on 26/01/2014 at 16:00.Pushed by hpereiradacosta into branch '1.4'.


[/FONT][/COLOR]

---

