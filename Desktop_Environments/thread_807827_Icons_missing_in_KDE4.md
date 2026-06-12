---
title: "Icons missing in KDE4"
date: 2008-05-26
forum: Desktop Environments
---

### Post by vitorsouza on 2008-05-26
Hello,

I've made a clean install of Kubuntu 8.04 KDE 4 Remix and I noticed that a lot of icons are missing, even after I ran adept and upgraded the system to the newest packages. Some that I've noticed so far:

- /home folder
- /media folder
- MS office files (doc, xls, ppt, etc.)
- Yahoo IM icon in Kopete

Has anyone experience this? What's the workaround?

Thanks,

Vitor

---

### Post by maestrobwh1 on 2008-09-03
I have a similar issue... anything that is a *doc is a "?" and any means I would know how to change it seem not to exist.  Under right click --> properties, one can change the program preference to open it, but there is no way to change the actual icon that shows up in dolphin.  Oddly, if I use firefox, and have to uploade a file, the file manager that opens there will show the openoffice writer icon for these files.  Oddly, *ppt and *xls files show with their appropriate OpenOffice counterpart

It has been this way since I have experimented with KDE4 when it was a port on Gutsy.

---

### Post by sayakb on 2008-09-03
You may add icons to the oxygen icon theme by copying them to /usr/lib/kde4/share/icons/oxygen folder.

---

### Post by warhammerkid on 2008-09-03
I just did that and restarted X, but nothing happened. Oxygen has icons for application/vnd.ms-word, but not application/msword, which is the default mime-type for word documents. I copied the application-vnd.ms-word.png files to application-msword.png for all resolutions, but the question mark icon still shows up. Is there some way to change application/msword to application/vnd.ms-word or regenerate some icon cache to get the icon to show up?

---

### Post by maestrobwh1 on 2008-09-03
> **LinuxIsInnovation said:**
> You may add icons to the oxygen icon theme by copying them to /usr/lib/kde4/share/icons/oxygen folder.

That just makes an icon different or one to be assigned... which is useful information for me, as I did not know how to do that easily. 

The issue is that the *.doc extension does not get an icon assigned and there seems to be no way to have one assigned, so it doesn't really matter what I put in the folder... all of the other MS documents get assigned the appropriate OpenOffice icon automatically because it is the preferred program to open each file type. Somehow this gets skipped for the doc extension.  I have openoffice and koffice installed and anything with *.doc is a "?" icon.

---

### Post by maestrobwh1 on 2008-10-03
I am surprised that this is still not resolved.

> **warhammerkid said:**
> I just did that and restarted X, but nothing happened. Oxygen has icons for application/vnd.ms-word, but not application/msword, which is the default mime-type for word documents. I copied the application-vnd.ms-word.png files to application-msword.png for all resolutions, but the question mark icon still shows up. Is there some way to change application/msword to application/vnd.ms-word or regenerate some icon cache to get the icon to show up?

---

### Post by doorknob60 on 2008-10-05
Fix please? It's happening to me in Arch and it's really annoying -.-

---

### Post by maestrobwh1 on 2008-10-05
I have been trying to find a fix for this since Ubuntu got kde4 packages.  I have had suggestions that say things like "add icon to folder" but they are not understanding the issue.  AN ICON CAN'T BE ASSIGNED in the traditional way so it doesn't matter what is in the oxygen folder.  There needs to be a way as in kde4 to click properties and change the icon of a file type, or to use system control and assign one there.  None of these work.

---

### Post by Splondike on 2008-10-09
See my post in the [other thread]("http://backports.ubuntuforums.com/showthread.php?t=909349") for the solution.

---

### Post by maestrobwh1 on 2008-10-13
I made a shell script that handles this based on your post.  I ran it on two of my machines and when you log back into kde4, the msword *.doc icons now have an icon rather than a "?"

The proper directory for Ubuntu is /usr/lib/kde4/share/icons/oxygen

The script is attached.

---

