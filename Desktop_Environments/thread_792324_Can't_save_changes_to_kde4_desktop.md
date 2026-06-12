---
title: "Can't save changes to kde4 desktop"
date: 2008-05-12
forum: Desktop Environments
---

### Post by deadtom on 2008-05-12
Any icons that I delete, add or rename are reversed as soon as I log out. Probably a permissions thing but I'm not sure what folder or file contains that information for kde4 so I don't know what to change the permissions on.
Thoughts?

---

### Post by Xiong Chiamiov on 2008-05-13
Reset the permissions on the .kde4 folder in your home directory?

---

### Post by deadtom on 2008-05-13
It's already set to rwx------. I can't imagine that it would need to be write able by any user other than me.

---

### Post by Zorael on 2008-05-13
Can you make manual modifications in a terminal or a file manager to the directory that contains the files on your desktop? This directory should exist under your home directory unless you moved it. By default it is [FONT="Courier New"]~/Desktop[/FONT]. You can also check in System Settings -> About Me -> Paths to see the location.

There is a bug that prevents you from changing the desktop directory reference, which requires you to manually edit a file. From what I understand from your post, this is not what you're referring to, though.

---

### Post by deadtom on 2008-05-13
No, I haven't tried it editing the ~/Desktop folder via terminal but I can make changes to it in KDE3 just fine and the permissions on it are rwx as well.

What file would I have to edit to address the other bug you mentioned. Might be worth a shot.

---

### Post by Zorael on 2008-05-13
Please see [http://ubuntuforums.org/showpost.php?p=4949335](http://ubuntuforums.org/showpost.php?p=4949335).

---

### Post by deadtom on 2008-05-13
Hmmm... nope. That's not it. I checked ~/.config/user-dirs.dirs and there is no occurrence of **[$E]** anywhere and **XDG_DESKTOP_DIR** is pointed at $HOME/Desktop.

Any other ideas?

---

### Post by deadtom on 2008-05-13
On that same note. When I log into KDE4 it has icons on the desktop that are NOT on the desktop in KDE3 and they're all icons that I have deleted a while ago. If I delete them they just come back next time I log in to KDE4.
It seems to be pulling info about the desktop from some other location.

---

### Post by Zorael on 2008-05-13
Curious. I don't use KDE4 myself so I can only help troubleshoot.


Is there any content at all on the desktop? If so, we could search the partition for that and see where it is.

Is there any section in systemsettings or kcontrol in which you can change desktop paths, such as the kde3 one described in that post?

---

### Post by deadtom on 2008-05-13
Ok what I've got here is a plasma issue. I edited plasma-appletsrc and it has entries for the magically reappearing icons. I renamed it in hopes that plasma would generate a new one at login with the correct entries in it but of course the new file is identical to the old one.
So what next?

---

### Post by Zorael on 2008-05-13
Hmm. See [http://bugs.kde.org/show_bug.cgi?id=155241](http://bugs.kde.org/show_bug.cgi?id=155241).

---

### Post by deadtom on 2008-05-13
No joy there either. I deleted the entire .kde4 directory, logged out, logged in and the old icons are gone but I still can't make any changes to the desktop. I can add and remove items from the panel and those changes seem to stay but not to the desktop.
I opened up a terminal and brought up the contents of ~/Desktop and all of the icons matched BUT when I deleted an icon from the desktop and then did ls in the terminal, the file for the icon I just deleted still exists in ~/Desktop but doesn't show on my KDE4 desktop.
It would seem that plasma is not able to read or write to ~/Desktop.

---

### Post by Zorael on 2008-05-13
And if you rename/delete the ~/Desktop directory and relog?

Alternatively purge kde4 completely and then reinstall. Perhaps you've already done this, in which case, ignore me.
```
$ sudo aptitude purge kde4-core
$ mv ~/.kde4 ~/kde4backup
$ sudo aptitude install kde4-core
```

I also assume you have the 4.0.3 version installed?
```
zorael@sunspire:~$ apt-cache policy kdebase-runtime-bin-kde4
kdebase-runtime-bin-kde4:
  Installed: (none)
  Candidate: **4:4.0.3-0ubuntu2**
  Version table:
     4:4.0.3-0ubuntu2 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
```

---

### Post by deadtom on 2008-05-13
No I haven't done this yet. I'll give it a whack. I'll have to wait until I get home though since our network admin at my office will have a coronary if I connect my personal laptop to the network and start downloading huge files.
I'll post if this fixes it or not.

---

### Post by deadtom on 2008-05-13
Btw, this is probably the cause but for some reason I'm showing kde4-core is version 4.0.0 even though adept-updater has been downloading updates to kde4 pretty regularly lately.

Thanks for all your help here. It is greatly appreciated.

---

### Post by Zorael on 2008-05-13
kde4-core version shows as 3.3 for me, so I usually check that kdebase-runtime-bin-kde4 package. :>
```
zorael@sunspire:~$ apt-cache policy kde4-core
kde4-core:
  Installed: (none)
  Candidate: 3.3
  Version table:
     3.3 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
```

---

### Post by deadtom on 2008-05-13
Heh, you're right. I'm looking at the wrong thing. V 3.3 here also. Anywho I'll purge and reinstall kde4-core this evening and see how it does after that.

---

### Post by inportb on 2008-05-13
Oh yeah. I just renamed my Desktop folder to prevent widget-icons ;p

---

### Post by deadtom on 2008-05-13
Reinstalling kde4-core didn't fix it. I think I may just have to live without KDE4 for a while.

---

### Post by Zorael on 2008-05-13
I am, like most of us I wager, regarding 4.0.3 as rc3. It may be stable-ish as it is right now, but it still has some way to go before being desktop-ready.

I might've actually used it if I didn't get weird graphical corruption upon drawing of windows, such as when right-clicking the desktop for the first time, opening up the panel menu for the first time, opening up *random other app* for the first time, etc. Display errors irk me something fierce.

---

