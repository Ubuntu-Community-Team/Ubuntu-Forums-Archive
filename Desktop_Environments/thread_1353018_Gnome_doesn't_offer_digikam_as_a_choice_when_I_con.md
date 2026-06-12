---
title: "Gnome doesn't offer digikam as a choice when I connect my camera"
date: 2009-12-12
forum: Desktop Environments
---

### Post by reuben on 2009-12-12
What can I do to make digikam be offered as a choice by Gnome when my camera is connected? I find digikam to be far superior to f-spot, so I don't want to switch.

Gnome will pop up the "what do you want to do with this" dialog, but (now that f-spot is uninstalled, and despite digikam being installed) the dropdown is empty and unselectable.

---

### Post by kellemes on 2009-12-12
From Nautilus?
Edit -> Preferences -> Media -> Photos maybe? (not selectable in my case, don't know why)
Just guessing..

---

### Post by reuben on 2009-12-12
Good guess. Unfortunately digikam isn't listed in the applications list (and, some software is listed multiple times...e.g. okular.) Sometimes I miss KDE.

---

### Post by ypout on 2009-12-13
I have the same issue - I have gotten this to work in the past by tweaking gconf but in Karmic the Keys I changed are no longer available :(


OK I got it to work as follows:
Open Nautilus | Preferences | Media
Select Open with Other Application under Photos
Select the Use a custom command option
Enter digikam --download-from %m
Click Add

Now when I plug in my XdCard Digikam opens at the download window

---

### Post by kellemes on 2009-12-14
> **ypout said:**
> 
Select Open with Other Application under Photos


For some reason it's gray in my case, I cannot select anything.. eventhough I have Digikam installed and other packages that can handle photo's.

---

### Post by reuben on 2009-12-14
Thanks, that worked for me.

---

