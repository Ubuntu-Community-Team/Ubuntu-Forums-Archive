---
title: "Is there a way to set the toolbar at the bottom back to default?"
date: 2009-07-13
forum: Desktop Environments
---

### Post by NinjaNumberNine on 2009-07-13
Hi, I have Kubuntu 8.10. My question is, is it possible to fix the toolbar at the bottom of the screen once you scramble it? I *accidently* #-o clicked something and it shut down the whole panel. I tried setting it back up piece by piece from Add Widgets, but this insists that the widgets spread out and cover the whole toolbar, so now when I minimize an app it vanishes.



Thanks in advance,


        NinjaNumberNine

---

### Post by BbUiDgZ on 2009-07-13
> **NinjaNumberNine said:**
> Hi, I have Kubuntu 8.10. My question is, is it possible to fix the toolbar at the bottom of the screen once you scramble it? I *accidently* #-o clicked something and it shut down the whole panel. I tried setting it back up piece by piece from Add Widgets, but this insists that the widgets spread out and cover the whole toolbar, so now when I minimize an app it vanishes.



Thanks in advance,


        NinjaNumberNine

when you go to login start a new session at login screen.

---

### Post by twright on 2009-07-13
You could try deleting the appropriate .files in your home folder (show hidden files to show them) and when you log in again it will be restored to its default state

---

### Post by NinjaNumberNine on 2009-07-13
> When you go to login start a new session at login screen.     Thanks for reply, but unsuccessful. 

> You could try deleting the appropriate .files in your home folder (show hidden files to show them) and when you log in again it will be restored to its default stateAs for this, I am a Linux Beginnux. I have attached a screenshot of my home folder. Could you tell me which file or folder to delete?

Thanks all!

---

### Post by Zorael on 2009-07-13
> **NinjaNumberNine said:**
> As for this, I am a Linux Beginnux. I have attached a screenshot of my home folder. Could you tell me which file or folder to delete?
**.kde** > **share** > **config**, files beginning with **plasma**. I think it's plasma-desktop-appletsrc, but I'm not sure. You'd need to log out to see the changes take effect.

There's actually a chance the files will be recreated as plasma closes (when you log out), which makes this a bit tricky. If so, you'd need to close plasma first, then delete/move those files and restart it again.

I think you can get a task manager to pop up if you hit ctrl+esc; if so, the plasma process is called **plasma-desktop**. Else hit alt+f2 and enter '**kquitapp plasma-desktop**', that should close it. Do your thing, then hit alt+f2 and enter '**plasma-desktop**' when you're ready to restart it.

---

### Post by NinjaNumberNine on 2009-07-13
[SIZE=7]:pOH YEAH!:p
It worked!!
THANKS!
[SIZE=4]I didn't even have to logout!
You guys are great!
[/SIZE][/SIZE]

---

### Post by twright on 2009-07-13
Glad you got that working :-) Sorry I could not have been more specific earlier (I am mostly a gnome user myself)
> **NinjaNumberNine said:**
> [SIZE=7]:pOH YEAH!:p
It worked!!
THANKS!
[SIZE=4]I didn't even have to logout!
You guys are great!
[/SIZE][/SIZE]

---

### Post by NinjaNumberNine on 2009-07-13
Yeah. GNOME is stable, and KDE is beautiful.

---

### Post by izizzle on 2009-07-13
> **NinjaNumberNine said:**
> Yeah. GNOME is stable, and KDE is beautiful.

I think I can see where this thread is going to go from here. Just forgive the guy and move on...

---

### Post by NinjaNumberNine on 2009-07-13
Okay, change of directions. can someone help me [[COLOR=Red]**here?**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1211669")

---

