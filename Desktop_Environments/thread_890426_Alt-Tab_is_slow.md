---
title: "Alt-Tab is slow"
date: 2008-08-15
forum: Desktop Environments
---

### Post by alex1973 on 2008-08-15
Sometimes a month ago I have noticed that Alt+Tab switching is very slow. It takes around 2 seconds to switch between 2 applications on my HP 8510p (Core 2 Duo2.4Ghz, 3G mem., Radeon hd2600) running Ubuntu 8.04.1. The system is up-to-date and includes "Pre-released updates".
I found an old thread complaining about the same problem. ([http://ubuntuforums.org/showthread.php?t=26228](http://ubuntuforums.org/showthread.php?t=26228)). Using the mouse the switch is fast.

Thanks for your help.

---

### Post by Margate on 2009-05-24
I had same experience, any actions when switching between windows (except mouse click) resulted in very slow performance, I believe functions such as ALT-TAB involve compiz. Anyway; I remembered that I a few days ago installed Skype and along with that some required qt4 libraries. Removing Skype didn't change anything, Removing qt4 libraries fixed my performance issues using ALT-TAB.

Kind Rgds.
Margate

Versions
Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

---

### Post by darthnuri on 2009-08-27
Are you using on board video? I have the same issues and I'm using Intel GMA 4500 video chipset.

---

### Post by Steenreem on 2010-03-08
I too have a very slow alt+tab in linux mint. I'm running a modern dual core processor, and a HD Radeon 4850 graphics card with 4GB memory. Alt+tabbing between simple applications can take a second. This must be some bug. I'm using compiz and I'm a linux noobie.

---

### Post by jerwilkins on 2010-06-08
Same for me. Brought it up in another thread, but it sounds like this is an identical issue, albeit a very old one.

---

### Post by C. M .Hughes on 2010-09-21
Does anyone have a fix for this yet?

---

### Post by C. M .Hughes on 2010-09-26
I think I've found a fix (at least for my machine). The problem was with compositing.

I disabled it using

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

or, graphically:

Press Alt-F2 to open the Run Application dialog. Type gconf-editor and press enter. Navigate to apps->metacity->general and use the compositing_manager option.

It seemed that when it was enabled my alt-tab was trying to generate a live preview- I guess my machine struggled with it.

---

### Post by 3Miro on 2010-09-26
Here is what would do:

1. Older ATI cards have somewhat poor support for Linux (pre AMD, ATI did not care much about the FOSS community). I have gotten better performance on my ATI without the proprietary drivers enabled. System -> Admin -> Hardware Drivers, disable it and see if this help.

2. For Intel and weaker ATI, if you are running too many effects, the entire system will slow down too much. If you are using compiz, install ccms (look for it in the Software Center) and remove many of the animations. You can also disable ring and shift switchers and leave only application switcher. This should improve performance for everything.

3. If you are using Metacity, you can use gconf-editor (Alt + F2 then run the command) to edit Apps -> Metacity -> General and enable/diable composition depending on which one works better for you.

---

### Post by maxmk on 2010-10-29
I was facing the same problem after installation a Theme.. but now all working fine again.. Thank you guys

---

### Post by kitofr on 2011-05-13
Hade the same issue... changed to the recommended graphics drivers and rebooted. After that everything was fine and dandy :popcorn:

---

### Post by 1jackjack on 2011-06-05
I was having this problem with Natty recently. The solution turned out to be very simple - a simple compiz setting. I wrote a [blog post]("http://www.only10types.com/2011/06/ubuntu-1104-natty-slow-alttab-window.html") about it.

---

### Post by mrxtravis on 2012-01-04
> **C. M .Hughes said:**
> 
Press Alt-F2 to open the Run Application dialog. Type gconf-editor and press enter. Navigate to apps->metacity->general and use the compositing_manager option.


This works for me.

---

### Post by olilo on 2012-01-18
> **C. M .Hughes said:**
> I think I've found a fix (at least for my machine). The problem was with compositing.

I disabled it using

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```


Did the trick. Thanks.

---

### Post by Redsandro on 2012-02-13
I have this annoying problem too. Using XFCE (Xubuntu-desktop) on Ubuntu 11.10 with compiz.

BUT

It all works perfectly on my laptop with Intel chipset (@ Core i3). Compiz animations, alt+tab, perfect. 

However, when I attach an external monitor via HDMI (and even if I turn off the laptop LCD in XFCE settings) the alt+tab suddenly has a ~ 2 second delay. After I alt+tabbed 1 time, it goes fluently. But when I stop alt+tabbing, after ~ 10 seconds it takes ~ 2 seconds again.

AS IF it needs time to create thumbnails. But it only happens with the monitor attached. I think it's not a video driver issue, because any crazy animated ring selector or window switcher works perfectly fine and instant. I'd just really like my alt+tab back, especially since it didn't write me a good excuse note.

---

### Post by Redsandro on 2012-02-13
Guess was right! When using icons instead of thumbnails for the windows, it's instant again! WHY would this suddenly become a problem with a second monitor attached?

The default panel without problems is 1366 pixels wide, the monitor is 1920 pixels wide. Would that really be the trouble?

Alt+tabbing with only icons is not very 21st century. :P

---

