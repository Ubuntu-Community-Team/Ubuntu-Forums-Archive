---
title: "Background list"
date: 2013-12-19
forum: Desktop Environments
---

### Post by jason13 on 2013-12-19
One thing that's bugged me about 12.04 is that my list of desktop backgrounds doesn't stay populated with previous pictures. They're all stored in a subfolder of /home/user/pictures. I'd like to keep the list populated each time I open the desktop backgrounds window.

---

### Post by tgalati4 on 2013-12-19
I'm pretty sure that /usr/share/backgrounds is the only directory that gets scanned for the backgrounds selection dialog.  So you can either put some pictures there--which requires sudo privilege, or perhaps put a link in that directory to your pictures directory so that gets scanned as well.

There should be a way to change it.  I couldn't find it in *gconf-editor*.  So someone else (smarter than me) will have to help you.

I made a symbolic link in /usr/share/backgrounds which pointed to my ~/Pictures directory, but it didn't get picked up.  So that is a dead end.

On this laptop, I'm running Linux Mint (based on Jaunty) with an older Gnome2 desktop.  The background references are stored in .gnome2/backgrounds.xml.  The wallpaper-changer dialog manages this file and adds to it as you select images to your background/wallpaper collection.

There are several wallpaper managers:

```
apt-cache search wallpaper
```

So other than a simple scan of /usr/share/backgrounds, the default desktop environment does not dynamically scan a user directory for wallpapers to select from--or randomly display.

---

### Post by deadflowr on 2013-12-20
I know not how the system scans the home pictures folder.
But you can create an .xml file and place it in the folder
/usr/share/gnome-background-properties.
This is the file that reads what pictures are the wallpapers.
It doesn't matter where the pictures are, as long as the paths in the file are right.
(The default, of course are the pictures in the /usr/share/backgrounds folder)
The name of the .xml file can be anything, as long as it sits in the above mention folder.
This might help in adding your folder to the list
[http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers](http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers)

---

