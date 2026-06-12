---
title: "Missing icons in GNOME"
date: 2004-11-29
forum: Desktop Environments
---

### Post by vaskark on 2004-11-29
[font=Trebuchet MS]I've been using ubuntu since it came out and it is really sweet. However, when I last logged in several of my icons in the GNOME Menu are suddenly missing, and on the panel too. I received error messages about not having permissions. I tried to add them back, and the files are still there but this is what I found:
  
  [color=Gray]root@warty /usr/share/icons/hicolor/48x48/apps # ls
  ls: gnome-audio.png: Input/output error
  ls: gdm.png: Input/output error
  ls: file-manager.png: Input/output error
  ls: gdict.png: Input/output error
  ls: gnome-desktop-config.png: Input/output error[/color]
  
  ... etc
  
  I guess I need to know what package I need to re-install thru synaptic. Does anybody know? Thanks.
  
  [/font]

---

### Post by wallijonn on 2004-11-29
Let me guess - you were trying to install a .theme or .icons. 

What happens if you right click the task bar and add an app.?

What hapens if you [COLOR=Blue]Computer -> Desptop Preferences -> Theme[/COLOR] ?

---

### Post by vaskark on 2004-11-29
Actually, I wasn't doing anything of the kind, which is why this is a big mystery. The next time I rebooted things got even worse: a hard drive checked failed, and I had to use 'fsck' to fix a bunch of settings (something to do with ionodes ???). Anyhoo, once I got thru that it booted properly and I was back into GNOME. This time I noticed that some of the menu icons had returned, but not all (most of Desktop Preferences are still missing). I tried changing the icon theme but they were still gone.
  
  I guess I should go to **preferences-all-users:// **and re-assign the icons, but I'm starting to believe that some icons in **/usr/share/icons/hicolor/48x48/apps** are missing. If they are what's the best way to re-install them?

---

### Post by vaskark on 2004-11-29
K, I downloaded the gnome-icon-theme tarball and copied over all the 48x48/apps/ icons. That seems to have done the trick. Still don't know why this happened, tho - I was trying to get MPlayer to work with dvd's at the time this occurred.
   [img]http://www.ubuntuforums.org/images/smilies/eusa_wall.gif[/img]
  
  Thanks anyway.

---

### Post by dtessier on 2004-11-30
[QUOTE=vaskark]root@warty /usr/share/icons/hicolor/48x48/apps # ls
ls: gnome-audio.png: Input/output error
ls: gdm.png: Input/output error
ls: file-manager.png: Input/output error
ls: gdict.png: Input/output error
ls: gnome-desktop-config.png: Input/output error[/QUOTE]This type of error occurs when the directory in the filesystem contains entries pointing to some files, but the files themselves are not actually there.

[QUOTE=vaskark]Actually, I wasn't doing anything of the kind, which is why this is a big mystery. The next time I rebooted things got even worse: a hard drive checked failed, and I had to use 'fsck' to fix a bunch of settings (something to do with ionodes ???). Anyhoo, once I got thru that it booted properly and I was back into GNOME. This time I noticed that some of the menu icons had returned, but not all (most of Desktop Preferences are still missing). I tried changing the icon theme but they were still gone.
  
  I guess I should go to **preferences-all-users:// **and re-assign the icons, but I'm starting to believe that some icons in **/usr/share/icons/hicolor/48x48/apps** are missing. If they are what's the best way to re-install them?[/QUOTE]Combined with the fsck occuring on reboot, I'd say you experienced some disk corruption, and this is why some of your icons are missing.

---

