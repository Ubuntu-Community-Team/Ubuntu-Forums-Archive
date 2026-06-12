---
title: "What do you use for your taskbar/toolbars?"
date: 2006-05-15
forum: Desktop Environments
---

### Post by elamericano on 2006-05-15
I have tried to clean up my taskbar, but I can see that there isn't going to be enough space for everything I want to display. I have seen improved taskbars, Mac OSX type docks, and extravagant replacement menu systems, but I am wondering what people use for efficiency over eye-candy.

One specific taskbar question, I decided to hide the clipboard and catapult icons in the system tray, but there's a giant arrow and blank space to the left of it that takes as much space in total as the two icons I'm hiding. Does anyone know an option to delete from the tray instead of hiding? Or hide the "hide" arrow? :rolleyes: 

I think I'd like to have my taskbar separate from my apps and custom launchers, 'cause they tend to be full most of the time, but I don't know how to add another toolbar for menus, appletts, and apps. Again, I'd like to hear what the knowledgable folks in this forum have chosen from personal experience. Searching has been hard with this topic - either I find too much information, or none at all.

Thanks.

---

### Post by userundefine on 2006-05-15
Try [these]("http://ubuntuforums.org/showthread.php?t=77694").

---

### Post by elamericano on 2006-05-15
KDE, my friend, not Gnome.

Also, looks more cool than useful. I usually don't hide that much stuff. I figure if it's hidden too much, then it probably doesn't deserve to be on my toolbar. A lot of stuff gets banished to the menus.

---

### Post by link141 on 2006-05-15
(sorry if this is confusing, don't know how to quote correctly)  For your sys tray question, you can **quit** an application by right clicking and selecting quit.  **Your profile says you are running Ubuntu not Kubuntu, I have Kubuntu on my system 'cause Gnome is not nearly as customizable as KDE.  The following assumes you have Kubuntu.** For you question of how to add another panel, (the KDE version of a windows taskbar, in KDE the taskbar is the part of the panel that allows you to see your open windows) right click your main panel and go to add to panel (I'm running Dapper so it may be different) panel.  A new panel should appear right above your existing one, you can move either by dragging it to the top of the screen, or by right clicking the panel and selecting configure panel.  A window will pop up with the panel settings, it's pretty intuitive to set up.  I'll include a picture of my desktop attached to this post (it should work).  If you decide to up switch to Kubuntu, I'd reccommend using Dapper Drake, it's more stable.  Sorry I rushed the authoring of this post, but it's pretty easy to set up your desktop.  Thanks for reading :).

---

### Post by elamericano on 2006-05-15
Bloody marvelous!

The extra panel was what I wanted. (not just the external taskbar) So, I added the panel and tasks and a few other items. Now I have plenty of space for my application icons. What I ended up with was very close to your screenshot. I tried not to have a Gnome bias in where I thought things should go, but I have to give them credit for having excellent defaults, whereas KDE gets points for being configurable. Anyway, I'm "trying out" kubuntu for a while, so I am technically still a ubuntu user. (I wonder how many ubuntu users never give KDE a testdrive. This side of the forums definitely seem slower - not that that will factor into my decision)

The last two things I'd like to change are:

1) Erasing, nuking, or otherwise removing klipboard and catapult from the tray (or hiding them without the giant arrow icon saying they're hidden.)

2) My clock displays Time - Date, but I want Date - Time. It changed all by itself when I was experimenting with formats, now I can't get it to go back to how it was right after install.  Default is digital time, so deleting and restoring the clock didn't work. Odd one isn't it?

---

### Post by elamericano on 2006-05-15
#1 is solved by simply exiting the apps. Klipper asks if it should run on startup. Katapult doesn't, but neither one came back. Previously I tried configuring the tray and renaming the klipper.png icons, but that hadn't worked. I guess I was overthinking it.

#2 I deleted the config rc files for clock under ~/.kde, but it didn't change the behavior. The order changed when I changed system date format to mM-dD-YYYY. For now, I'll remove date, but I'd sure like to fix this.

---

### Post by elamericano on 2006-05-16
Well, #2 goes back to Date before Time, if I return the format to YYYY-MM-DD. I'd like to stay that way for mM-dD-YYYY too, but there you are.

Thanks for everyone's help. I finally have a good starting point for my KDE test drive. Unfortunately, I've already had more crashes than is acceptable, but maybe that will improve in dapper. I've got mail, browsing, vi, rdp, vnc, and wireless, so I'm good to go.

---

### Post by link141 on 2006-05-16
Just some advise.  I've had **many, many, many** problems that almost pushed me over the edge of sanity with Breezy.  Oh, that was a sad time...  I feel sorry for myself that I never tried Dapper when I was groping about Breezy.  But on contrary, when I tried Dapper, every single problematic piece of KDE that was causing me grief trying to fix, worked absolutely perfectly.  I couldn't believe it.  Be sure to try Dapper (when it becomes stable if you preffer) if you are running in to many difficult problems in the future.  This may prove a real headache saver in the future.  Glad to help, happy Ubuntu-ing :).

---

### Post by link141 on 2006-05-16
Sorry I was typing up a solution for you when my browser crapped out! I will post it in a few moments...

---

### Post by link141 on 2006-05-16
Here it is:
Almost forgot.  I you'd like to format MM-DD-YYYY , with your date, first right click on the date and select "Date and time format...".  A window will pop up labelled "Configure - KDE Control Module" , click the tab at the top labeled time and dates.  In the section labeled "Short date and time format"  enter MM-DD-YYYY from your keyboard, the drop-down menu is just for common presets.  Does that help?  Thanks for reading :).

---

### Post by elamericano on 2006-05-16
[QUOTE=link141]Almost forgot.  I you'd like to format MM-DD-YYYY...[/QUOTE]

Actually, I can change the date format to my preferred mM-dD-YYYY. The problem was that the Date is to the right of the time before the change, and after the change the Time is to the right of the date. I want my new format, *and* I want to keep my Time display in the right corner. I don't see any way to change this quirky behavior.

---

