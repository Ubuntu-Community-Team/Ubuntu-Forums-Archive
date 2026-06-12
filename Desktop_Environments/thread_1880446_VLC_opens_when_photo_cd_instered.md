---
title: "VLC opens when photo cd instered"
date: 2011-11-13
forum: Desktop Environments
---

### Post by Charlotte18 on 2011-11-13
In Ubuntu 11.10, Unity, when I insert a cd with photos, VLC media player opens. Also, when I click on the cd on the Unity launcher, VLC media player opens? How do I fix this problem?

---

### Post by David006 on 2011-11-13
Click on top-right corner of desktop ..

**System Settings >> Removable Media**


What do you want the settings to be?

---

### Post by Charlotte18 on 2011-11-13
System Settings > Removable media only takes care of the first problem: I can set a default action for what happens automatically, if anything, when I insert removable media.

How do I solve the second problem? Any removable media that I insert (CD, USB drive, etc) opens with VLC media player when I click its icon on the Unity launcher.

> **David006 said:**
> Click on top-right corner of desktop ..

**System Settings >> Removable Media**


What do you want the settings to be?

---

### Post by David006 on 2011-11-13
> **Charlotte18 said:**
> How do I solve the second problem? Any removable media that I insert (CD, USB drive, etc) opens with VLC media player when I click its icon on the Unity launcher.

In Nautilus (the file/folder viewer), right-click and choose 'open with' >> 'other application' ..  Try to select (and assign) the application you do want to start.

I suggest 'Shotwell' ..


If you need more detail, then describe in more detail what steps you are doing ..

---

### Post by Charlotte18 on 2011-11-13
Unfortunately, right-clicking on the icon of a removable media item (CD, USB, etc) and choosing properties (even within the /media folder) does not show the choice for "open with" as it does for other folders.

---

### Post by David006 on 2011-11-13
If you insert / plug-in removable media then VLC starts ..

OK.

Then close VLC, and go back to Nautilus.  Try to right-click on a file within the folders on the media (you inserted).

(Again.) Describe it to me in smaller / specific steps, and I will try to re-produce the issue.

---

### Post by Charlotte18 on 2011-11-13
Listen. We're talking past each other. 

When I insert removable media, VLC media player opens. I stopped this by going to System Settings > Removable media and checking the option to "do nothing."

Unfortunately, despite this "work around" (which is only covering the problem), when I click the icon of the removable media ***on the Unity Launcher***, VLC media player opens.

If I open the Home folder on the Unity Launcher and then click the icon for the media on the list of folders on the left, the media opens like a folder.  If I go to /media/cdrom and so on and double-click the icon, the media opens like a folder.  I want this behavior when I click on the icon in the Unity Launcher, but when I click the icon of the removable media ***on the Unity Launcher***, VLC media player opens.

---

### Post by stinkeye on 2011-11-13
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=11393051#post11393051")

---

### Post by David006 on 2011-11-13
Here is how I have my PC setup:

check 'Removable Media' settings

insert DVD

prompted to choose action

open Nautilus, click on icon

right-click on media file, choose ..

---

### Post by Charlotte18 on 2011-11-20
Thanks.  The instructions in that thread worked.

> **stinkeye said:**
> See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=11393051#post11393051")

---

