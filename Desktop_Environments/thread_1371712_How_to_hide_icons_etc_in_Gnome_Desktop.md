---
title: "How to hide icons etc in Gnome Desktop?"
date: 2010-01-03
forum: Desktop Environments
---

### Post by TheNessus on 2010-01-03
Hi all.

I want to hide objects, i.e. icons, files, etc from the desktop view in Gnome, just like it is by default with KDE. Why? because I use folderview screenlets, that work just like in KDE. It's just that I love how KDE looks, but I really hate KDE(4) itself. 

Any ideas?

---

### Post by darco on 2010-01-03
Open a terminal, type gconf-editor and hit enter.
Then navigate to apps/nautilus/desktop. There you can uncheck what is currently residing on your desktop.



darco

---

### Post by TheNessus on 2010-01-03
I have already deleted the trash and other default icons.

I'm talking about objects like files. I want the files to appear in the folder view of the desktop but no the desktop itself.

I turned off 'show desktop' in gconf, but it has some side effects I don't like.

thanks though.

---

### Post by mcduck on 2010-01-04
Sorry, but the only way is to disable Nautilus from showing the desktop (like you already did). Nautilus doesn't have any option for just hiding the icons.

Of course that means you'll loose both your wallpaper (you can use anther app to set a wallpaper) and the right-click menu on desktop.

Apart from that the only option I can think of is simply not putting any files in the Desktop directory. ;) Just use some other directory for your screenlet.

---

### Post by Janoka on 2010-10-22
I use Maverick (10.10)
Today after a normal reboot, all the folders in the Home directory appeared on my desktop. None of the above mentioned things don't work, in the gconf-editor the above mentioned checkbox is not checked. Checking or unchecking that checkbox makes no difference, the folders are constantly on the desktop.

I have no idea why they are there...
Any idea is highly appreciated. Thanks in advance.

---

### Post by rvchari on 2010-10-22
> **Janoka said:**
> I use Maverick (10.10)
Today after a normal reboot, all the folders in the Home directory appeared on my desktop. None of the above mentioned things don't work, in the gconf-editor the above mentioned checkbox is not checked. Checking or unchecking that checkbox makes no difference, the folders are constantly on the desktop.

I have no idea why they are there...
Any idea is highly appreciated. Thanks in advance.
i have the same problem since i upgraded from jaunty to lucid and now to maverick. i tried all the jugglery thats mentioned in the forum but no result !!! something must b wrong with nautilus ? i created another username and tried it there, everything is fine !!! wonder some small problem must b created which i m unable to identify.

---

### Post by rvchari on 2010-10-22
i even deleted the .nautilus from my home directory, logged out and re-logged just to check if the new dot file thats created works fine, still the same problem persists !!!:(

thanx in advance for help from forum members !!! m sure janoka will be happy too if this is resolved soon !

---

### Post by rvchari on 2010-10-22
i m attaching my maverick desktop logged on to desktop edition (netbook edition desktop is not viewed so no issue, only hitch is the right flick menu thats disabled in netbook edition)

---

