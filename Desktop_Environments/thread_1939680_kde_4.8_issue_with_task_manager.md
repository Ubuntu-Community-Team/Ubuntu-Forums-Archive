---
title: "kde 4.8 issue with task manager"
date: 2012-03-12
forum: Desktop Environments
---

### Post by mike.franky on 2012-03-12
Hi,

I just swapped from gnome to kde and upgraded to kde 4.8 . I must say that I am very impressed with it. However there seems to be a little problem. When I first boot the computer, there is a nice feature which allows the user to preview an application when he hovers over its taskbar icon. I am not talking about the thumbnail. I am talking about the feature that makes all the other applications transparent enabling you to see only the application whose icon you are hovering over on the taskbar.

For some reason, after a while I loose this feature! Does anyone know what might be going on?

Thanks in advance for any help!!

---

### Post by whatthefunk on 2012-03-12
Whats the name of that feature and how did you enable it?

EDIT: Just figured it out.

Right click on the task bar and open up Task Bar Settings.  Make sure that Highlight Windows is checked.  Im going to leave this on for a bit to see if mine breaks too.

EDIT #2: The Highlight Windows effect needs to be set in two different places: in the task bar settings mentioned above and in the normal settings menu at Workspace Appearance and Behavior > Desktop Effects > All Effects

---

### Post by mike.franky on 2012-03-12
Thank you very much for your help!

I am actually using the "icon-only" task manager which is available only on 4.8. The "highlight window" is indeed enabled! As I said, when I boot it actually works fine! The problem is that after a while it stops working by itself

---

### Post by whatthefunk on 2012-03-16
Hmmm....Ive had this on for nearly a week now and it still works fine.  Never had it break on me.  Have you done a bug search?  If its still giving you a problem, you could post on the KDE forums.

---

### Post by mike.franky on 2012-03-22
thanks and sorry for replying so late!!

How do I do a bug search? Btw if I disable the highlight window option and re enable it, the problem is fixed for the time and it breaks again after a while!! Also, I actually installed ubuntu (not kubuntu), then installed kubuntu-desktop and then upgraded to kde 4.8. Do you think that might have caused a few problems?

---

### Post by mike.franky on 2012-03-30
Just to give an update, I formated my computer and re-installed kubuntu on, upgraded to version 4.8 and the problem still exists! The highlight window functionality seems to stop working after a while and I have to disable and re-enable it in order to temporarily fix it.

Is no one else having a similar problem?

---

### Post by Erik1984 on 2012-03-30
You could search for it here: [https://bugs.kde.org/ ]("https://bugs.kde.org/")
edit: I tried to find some relevant reports for you but can't find the right terms to search for. So far no luck. Maybe you can file a new bug report there (you need an account for that).
[]("https://bugs.kde.org/")

---

### Post by gracerain on 2012-03-30
> **mike.franky said:**
> Hi,

I just swapped from gnome to kde and upgraded to kde 4.8 . I must say that I am very impressed with it. However there seems to be a little problem. When I first boot the computer, there is a nice feature which allows the user to preview an application when he hovers over its taskbar icon. I am not talking about the thumbnail. I am talking about the feature that makes all the other applications transparent enabling you to see only the application whose icon you are hovering over on the taskbar.

For some reason, after a while I loose this feature! Does anyone know what might be going on?

Thanks in advance for any help!!
I had the same problem with Icon-only taskmanager, the highlighting windows effcet disappears each time I use "Alt + Tab" to switch tasks

---

### Post by whatthefunk on 2012-03-31
> **gracerain said:**
> I had the same problem with Icon-only taskmanager, the highlighting windows effcet disappears each time I use "Alt + Tab" to switch tasks

Confirmed.  Same thing happens on mine.  Has anybody filed a bug report yet??

This doesnt appear to be a problem when you use the normal task manager...

Glad we figure this out!  Now we just need a fix.

---

### Post by mike.franky on 2012-04-03
Hi, 

Alt + Tab seems to be the problem for me as well. I would have NEVER found that one! Thank you all very much for you help! I hope the issue will be fixed soon!

Just for future reference, how does one report bugs?

---

### Post by mastablasta on 2012-04-03
for KDE bug see here: [https://bugs.kde.org/ ]("https://bugs.kde.org/")

for Ubuntu /Kubuntu: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

