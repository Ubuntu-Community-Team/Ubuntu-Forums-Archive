---
title: "Just upgraded to 8.10, annoying grey bar covering maximize, minimize, close buttons"
date: 2009-03-26
forum: Desktop Environments
---

### Post by imolafem on 2009-03-26
So I have pretty much successfully upgraded my KUbuntu 8.04 to Kubuntu 8.10.  The only problem I have is that this grey bar is across the top of my screen and I have to close my Windows by going to File -> Close every time.  If I want to minimize them, I have to do it from the system tray across the bottom.

How do I get rid of the grey bar at the top?  Right or left clicking on it produces no menus to do anything with it.

---

### Post by hansdown on 2009-03-26
Hi imolafem.

Try hitting f11 twice, then restart firefox. This has worked for a number of people.

---

### Post by imolafem on 2009-03-26
Thanks for the tip, but it didn't work.  When I hit F11 and Firefox went to full screen mode, this grey bar still covered its features.  Going back to regular mode and closing and re-opening firefox did not affect the grey bar either.

Its almost like its the gnome menu bar up there without any buttons on it?

---

### Post by hansdown on 2009-03-27
Ther is an ongoing thread that indicates this is happening to other people.

[http://ubuntuforums.org/showthread.php?t=1094131](http://ubuntuforums.org/showthread.php?t=1094131)

---

### Post by imolafem on 2009-03-27
Thank you for your response.  It seems their problem is different than mine.  They have an issue with their title bars disappearing -- where as my screen has a constant grey bar across the top that will cover the title bar if the window is maximized.  My issue seems to be a constant single grey bar, whereas their issue seems to follow them around on each window.

I'm having the problem under KDE.  When I loaded Gnome, I do not have this issue.

---

### Post by imolafem on 2009-03-27
Here is a screenshot after I used FreeNX to connect in.  Notice the grey bar at the top just under my Windows bar with the minimize, maximize, and close buttons?  This is the bar in KDE I can't get to go away.

---

### Post by GeneralZod on 2009-03-27
> **imolafem said:**
> Here is a screenshot after I used FreeNX to connect in.  Notice the grey bar at the top just under my Windows bar with the minimize, maximize, and close buttons?  This is the bar in KDE I can't get to go away.

Can you post a bigger screenshot? This looks very much like a blank Plasma panel, but it's hard to tell.

Edit:

Also, please ensure the next screenshot has a KDE app open so we can see how windows are affected.

---

### Post by imolafem on 2009-03-27
Here you go....Thanks for looking at it!

It seems that the image gets much smaller when uploaded to the forums as an attachment.  I can upload to a website if its still hard to see.

---

### Post by GeneralZod on 2009-03-27
> **imolafem said:**
> Here you go....Thanks for looking at it!

It seems that the image gets much smaller when uploaded to the forums as an attachment.  I can upload to a website if its still hard to see.

That's pretty hard to see, so uploading it somewhere would be better :)

Can you right-click on the grey bar and, if so, does anything happen?

Can you open up a konsole terminal and type

```

kwin --replace

```

and let us know what happens?

---

### Post by imolafem on 2009-03-27
When I left or right click on the grey bar, nothing happens.

When opened a console and typed kwin --replace, then entire screen redrew itself including the grey bar.

The terminal says KDecorationPlugins::loadPlugin: kwin : path "/usr/lib/kde4/kwin3_ozone.so" for "kwin3_ozone"

---

### Post by imolafem on 2009-03-27
Here's one of the screenshots that are uploaded.

[http://www.fourcircles.net/gallery2/main.php?g2_itemId=6505&g2_imageViewsIndex=1](http://www.fourcircles.net/gallery2/main.php?g2_itemId=6505&g2_imageViewsIndex=1)

---

### Post by abn91c on 2009-03-27
you probably installed the wrong version of dekorator, you need to get it from adept manager, the package is called kwin-style-dekorator, make sure is the KDE4 version

---

### Post by imolafem on 2009-03-27
I installed kwin-style-dekorator from Synaptic and it was the KDE4 version.  It was not installed previously.  However, if I run kwin --restart from the Konsole, it still gives the same feedback and the grey bar is still at the top of the screen. 

I also rebooted to see if it would fix it after the install, but it did not.

---

### Post by SunnyRabbiera on 2009-03-27
It almost looks like its a part of your OS there, maybe there is a setting in your VM that is causing your issue.
VM's do have interesting issues sometimes.

---

### Post by imolafem on 2009-03-27
This isn't a VM.  Its running on an old Proliant ML110 tower server.

---

### Post by lsiden on 2009-04-07
I have the exact same problem.  You can still grab the title bar by moving each window by grabbing any part of it with your left mouse button while holding down the alt key.  But it's still annoying as all f@#$ck! as it robs me of valuable screen space.

---

### Post by imolafem on 2009-04-07
No one has yet responding with a solution.  In the meantime I installed gnome and that works just fine.

---

