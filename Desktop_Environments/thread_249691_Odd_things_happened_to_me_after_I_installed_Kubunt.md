---
title: "Odd things happened to me after I installed Kubuntu desktop over Dapper"
date: 2006-09-02
forum: Desktop Environments
---

### Post by dwasifar on 2006-09-02
I decided to try Kubuntu Desktop.  Used Synaptic to install the kubuntu desktop package and all its dependencies.

At first everything seemed fine.  Applications were taking a little longer to load, but not too bad.  I had set up a couple of desktop icons and was fooling around with appearance settings when suddenly things just seemed to go to hell in a handbasket.  

First the screen flashed, and my desktop icons were gone.  Then I started hearing a lot of disk activity.  The appearance settings window was blank white and frozen.  Opening apps, menus, or windows kept taking longer and longer.  I looked at the process monitor but I couldn't see anything that would be responsible for the disk activity.  I closed the session and started a new one; same thing.  I rebooted; same thing still continued to happen.  At one point the desktop wallpaper vanished to plain black.  

Finally the machine became so obsessed with whatever it was doing with the disk that it would not respond to menu or mouse clicks at all.  I had no option but to power it down and restore the previous system state from backup.  (Yes, I always have a backup!)

WTF?  I felt like I was working on a Windows box.  :confused:

---

### Post by aysiu on 2006-09-02
When you were "fooling around with appearance settings," were you in KDE or Gnome?

---

### Post by dwasifar on 2006-09-02
> **aysiu said:**
> When you were "fooling around with appearance settings," were you in KDE or Gnome?

I was in KDE, using KDE's controls.  Specifically, I was changing fonts.  I had also recently installed the MS core fonts.  They looked ugly in Gnome and I was trying to see if they looked any better in KDE.  (They don't.)

---

### Post by aysiu on 2006-09-02
Yup. Unfortunately, that does happen. I forget what icon set it was, but one time I installed an icon set in KDE and Konqueror kept showing up blank. I had to actually reset my KDE settings to get KDE back to normal. One of my favorite KDE styles (Domino) actually crashes KControl if I try to adjust my display settings while using the style (doesn't happen for other styles).

I don't know if it has to do with the theme creators not creating the themes right or something to do with the way KDE is constructed that makes it delicate... maybe it's a little of both. I've never had a theme actually freeze up the computer, though.

Usually a simple ```
mv ~/.kde ~/.kde.old
``` does the trick.

---

### Post by dwasifar on 2006-09-02
> **aysiu said:**
> Yup. Unfortunately, that does happen. I forget what icon set it was, but one time I installed an icon set in KDE and Konqueror kept showing up blank. I had to actually reset my KDE settings to get KDE back to normal. 
Hmmm.  I think I also tried to change icons, now that you mention it.  I wonder what it was trying to do with the disk?

---

### Post by aysiu on 2006-09-02
> **dwasifar said:**
> Hmmm.  I think I also tried to change icons, now that you mention it.  I wonder what it was trying to do with the disk?
No idea.

---

