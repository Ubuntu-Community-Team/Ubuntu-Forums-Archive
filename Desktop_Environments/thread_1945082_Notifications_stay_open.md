---
title: "Notifications stay open"
date: 2012-03-22
forum: Desktop Environments
---

### Post by Chip88 on 2012-03-22
Hey there!

Since I installed Kubuntu 11.10, the pop ups with the notifications (in the lower right corner) stay always open, until I close them with the "X".

To make more clear, which notifications I mean, I attach a screenshot.

Although there is a possibility - by right clicking on the "i" - to change the settings for notifications and the option is selected for "Auto - hide" (where it says "Automatisch ausblenden" in the second screenshot), they still stay open.

Thank you in advance for all your help!
(And sorry, that the screenshots are in German.)

Chipy

---

### Post by perspectoff on 2012-03-22
System -> System Settings -> Application and System Notifications -> Launch Feedback -> Enable Taskbar notification -> Startup notification timeout: 2 sec

This worked for me when I had similar frustrations (in addition to the Notifications Settings -> "Automatically hide" option found when right-clicking on the Notification icon ("i") in the system tray).

---

### Post by Chip88 on 2012-03-22
Hey perspectoff!

Thanks for your fast answer, but it doesn't work with me. :(

I even disabled the option in System -> System Settings -> Application and System Notifications -> Launch Feedback -> Enable Taskbar notification and they still appear and don't hide automatically.

There should be another solution...

---

### Post by Chip88 on 2012-03-24
Hey there!

Anybody has a new idea maybe?!

This makes me crazy!!!

---

### Post by Chip88 on 2012-03-26
Hey there!

I tried again some settings with those notifications. I realized that notifications of copy, move or delete appear in a pop up over the "i" and auto hide themselves after 10 - 12 seconds.

If I mount an pendrive or an extern hard disk, the **Device Notifier** opens in a pop up, but it doesn't auto hide itself, until I make a click to a window or on that pop up.

While searching in the internet, I found that it was once possible to insert the time in the "Device Manager Settings"; have a look [http://kde-apps.org/CONTENT/content-pre1/106051-1.png](http://kde-apps.org/CONTENT/content-pre1/106051-1.png) .

How can I change this now with Oneiric??? It has to possible...!!!

I found also: [https://bugs.kde.org/show_bug.cgi?id=262184](https://bugs.kde.org/show_bug.cgi?id=262184) and [http://osdir.com/ml/kde-commits/2011-11/msg00189.html](http://osdir.com/ml/kde-commits/2011-11/msg00189.html) .

It seems that somebody had the same problem as me there and the could resolve / fix it, but unfortunately, I don't understand what to do exactly. Maybe anyone here can give me some more clear instructions what to do and where (e. g., which files to edit!), please?!

Thanks in advance!

Chipy

---

### Post by SeijiSensei on 2012-03-26
Apparently the control for this has been relocated in later versions of KDE.  Take a look in System Settings > Application and System Notifications > Launch Feedback.  You'll see a setting for taskbar notifications.  I'm running the Precise (12.04) beta where the value defaults to 30 seconds.

The bug reports you referenced were targeted at the KDE developers.  According to the first one from bugs.kde.org, the problem was fixed about a year ago.

There is no longer a Device Manager applet, at least not in the version of KDE (4.8.1) that Precise uses.  I'd have to scare up another machine here to see whether that was true for Oneiric.

---

### Post by Chip88 on 2012-03-26
Hi SeijiSensei!

Thanks for your answer! Great!

I think you ment the following settings (see attachment, please; it's in German).

But, I disabled the 30 seconds at all. Even if it is enabled, it doesn't effect the device manager (or however you want to call it).

Those 30 seconds make just appear in my systray (see attached file in the red border; you call the "black thing" like this?), that a programme is going to start. If it is disabled, the programme just starts and appears in the systray.

Any further ideas?!

Regards,
Chipy

---

### Post by Chip88 on 2012-03-28
Anyone no idea???

---

### Post by Chip88 on 2012-03-29
Hey there!

I found out some more details about my "problem".
We have another computer where Kubuntu Oneiric 11.10 is installed. Connecting my usb or external drives there, opens the pop up of the device notifier.

Then it autohides after a few seconds, if I dodn't take any action.

I checked the setings of the taskbar and the device notifier and they're equal on my notebook and on the other computer!

So my question is: HOW can it be, that two computers with the same system have different behaviours with one widget???

As mentioned above, it HAS TO be a problem with the device notifier - widget, because the "normal" notification of the system (after copy, paste, ...) appear and autohide as they should!

Thanks in advance!
Chipy

---

### Post by SeijiSensei on 2012-03-29
One thing you can try is creating another account and logging in with that.  If you don't have the same notification behavior, then your problem must have to do with the KDE settings in your home directory.

---

### Post by Chip88 on 2012-03-29
@ SeijiSensei:

Thanks again for your help. It seems you're getting my personal problem solver. :KS

Well, I read also in another place about creating another account and logging in with that.
&#8594; BUT: It seemed very strange to me, because I just installed a really fresh and clean version of Kubuntu 11.10 about 1,5 weeks ago. After the installation I didn't change almost no setting...

&#8594; BUT 2: **Good news!!! Problem solved finally!!! ;)**
I checked the version of kubuntu on the other computer we have. It was **KDE 4.8.0**.
I had installed on my notebook **KDE 4.7.4**.

After upgrading my system to **KDE 4.8.1** the problem is finally gone!!! CARAMBA!!! :guitar: :lolflag:

The notifier popups when inserting an USB or external drive and autohides itself after some seconds!!!

Thank you very much for all your help, guys!!!

Chipy

---

