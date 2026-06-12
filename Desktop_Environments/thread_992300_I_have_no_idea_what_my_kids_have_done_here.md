---
title: "I have no idea what my kids have done here"
date: 2008-11-24
forum: Desktop Environments
---

### Post by ldzeppelin on 2008-11-24
Ok, I have been dabbling in Linux for some time but have been moving more and more torwards a jump from windows.  I like the way Ubuntu is done and have actually set up a couple of computers with it.  My main problem in the past was always 1) Wireless networking 2)Streaming media from on PC to the next. With Ubuntu and even Xubuntu I was able to set it up much easier than I could my wife's work Vista laptop (I will NEVER use Vista!).

Now for my problem. My kids computer has been running Xubuntu for a while.  The other day I went to help one of them do something and somehow they've messed with the window sizes. To give an example, the desktop looks the same (more or less) but when you open up a window such as Firefox, it will only occupy about a quarter of the screen at most and tries to "squish" stuff to fit the window. You can't move the window around or even minimize it anymore.  I have messed and messed and messed and just can't figure out how to change it back to default!  Am I going to end up redoing the install?  I really hate to, but will.  Also, what is the best way to keep the little buggers from doing something like this again? I need to keep the desktop easy enough that a 5 year old can get it going but the 2 year old can't sneak over when no ones looking and mess with it.

Thanks! Shawn

---

### Post by malachi1990 on 2008-11-24
The window may have been maximized by default, which in ubuntu keeps you from moving it. Hope this helps.

---

### Post by Coreigh on 2008-11-24
Two questions: 1) Does this behavior apply to **ALL** applications or just some? 2)Are the window controls avaiable and not work, or don't show at all?
( _ [] X ; in upper right of window)

Third question can you effect any change by right-clicking the title bar and using the context menu?

One idea comes to mind if it is only *some* programs. A sessions or profile manger settings could it have been told to remember window settings?
I don't know how that would work and I was unable to duplicate your trouble, but it is an idea.

---

### Post by ldzeppelin on 2008-11-24
messing with right clicks I can find an option for full screen but when toggling it it just changes the way the menu looks.  The Firefox browser for instance stays about the size of a quarter of the screen.

Oh, by the way, I am using KDE as default with XUBUNTU

Thanks!

---

### Post by apmcd47 on 2008-11-24
> **ldzeppelin said:**
> 

Now for my problem. My kids computer has been running Xubuntu for a while.  The other day I went to help one of them do something and somehow they've messed with the window sizes. To give an example, the desktop looks the same (more or less) but when you open up a window such as Firefox, it will only occupy about a quarter of the screen at most and tries to "squish" stuff to fit the window. You can't move the window around or even minimize it anymore. 

Thanks! Shawn

XUBUNTU uses XFCE. I think in XFCE you can set up "maximise margins" so that maximised windows will not cover all of the screen (useful for leaving areas for icons or panels uncovered). If I'm right (which'll be a first :)) you should be able to change the margins setting in the desktop settings dialog to get things back to normal.

Andrew

In the time I posted this three more postings appeared including the fact that you use KDE on this XUBUNTU, in which case it probably doesn't apply :-(

---

### Post by ldzeppelin on 2008-11-24
> **apmcd47 said:**
> XUBUNTU uses XFCE. I think you can set up "maximise margins" so that maximised windows will not cover all of the screen (useful for leaving areas for icons or panels uncovered). If I'm right (which'll be a first :)) you should be able to change the margins setting in the desktop settings dialog to get things back to normal.

Andrew

My bad, that's what I meant, I was browsing another topic and KDE stole my thoughts.  I'll go try the maximise margins thing now.  I'll let you know. Thanks!

---

### Post by ldzeppelin on 2008-11-24
I'm probably just missing it but I don't see many options in the desktop settings.  I don't see that one, I'll look through settings for a bit to see if I can find it.

Thanks again.

---

### Post by ldzeppelin on 2008-11-24
I think I may just have to redo my install.  I hate doing that.  Makes me think of my win98 days!

---

### Post by Swagman on 2008-11-24
try right alt and plus or minus on the keypad first !!

---

### Post by sisco311 on 2008-11-24
> **ldzeppelin said:**
> I'm probably just missing it but I don't see many options in the desktop settings.  I don't see that one, I'll look through settings for a bit to see if I can find it.

Thanks again.

go to *Menu* -> Settings -> Settings Manager -> Workspaces and Margins -> Margins tab and set the margins(left/right/top/bottom) size to 0

---

### Post by ldzeppelin on 2008-11-24
> **sisco311 said:**
> go to *Menu* -> Settings -> Settings Manager -> Workspaces and Margins -> Margins tab and set the margins(left/right/top/bottom) size to 0

I don't have a margins tab in that. It just shows up a workspaces tab.

---

### Post by ldzeppelin on 2008-11-24
> **Swagman said:**
> try right alt and plus or minus on the keypad first !!

What is this suppose to do? It doesn't do anything when I try it. 


I don't know how kids seem to do stuff like this!  I've seem then do some doosies on winxp too!

---

### Post by Zorael on 2008-11-25
Quick interjection; before you do something drastic as wiping and reinstalling, just try creating a new user to have Xfce generate default settings for it. If all other attempts fail, you could then just migrate all the necessary stuff from your old user to your new one.

If your kids did something to cause this and they don't have superuser privileges, it's *certain* to be a change confined to the user's specific settings. Ergo, a different user should be unaffected.

Also, it would help if you could provide screenshots to give us a better idea of what it looks like.

---

### Post by mali2297 on 2008-11-25
Remove the hidden directories **.config**, **.cache** and **.local** from your home folder. That should reset most things to the default setting.

---

### Post by ldzeppelin on 2008-11-25
> **mali2297 said:**
> Remove the hidden directories **.config**, **.cache** and **.local** from your home folder. That should reset most things to the default setting.

Thank you very very much. This in fact did the trick quite well!

Again, thanks to all for their input.

Shawn

---

