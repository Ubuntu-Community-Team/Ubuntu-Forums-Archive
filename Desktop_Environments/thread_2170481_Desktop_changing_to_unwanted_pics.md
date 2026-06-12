---
title: "Desktop changing to unwanted pics"
date: 2013-08-26
forum: Desktop Environments
---

### Post by Allison_Mann on 2013-08-26
Hi everyone,

I recently installed wallch but was having some trouble with it -- specifically my wallpaper was changing to pictures I had not instructed it to (and to be honest had never seen before, I'm not sure where they were coming from). 

I've since uninstalled wallch but the problem persists. To fix it I've tried deleting all of the files from /usr/share/background and putting only those files I want as backgrounds in as well as editing /usr/share/background/gnome-background-properties/precise-wallpapers.xml but it still changes and I'm stumped. 

Any ideas on what may be causing this problem or how I could fix it?

Thanks!

---

### Post by grahammechanical on 2013-08-26
Do you have any images in the Pictures folder? We can set the Appearance utility to use images in the Pictures folder as background images. Open the Appearance utility and in the panel at the top of the box where the wallpapers are shown click on the drop down menu and make sure Wallpapers is showing in the panel and not Pictures Folder. I am not sure but I think that is how utilities like Wallch produce background image slide shows by putting them in the Pictures folder and changing the setting to tell Ubuntu to look in the Pictures folder for a background image.

Another thing to watch out for if you have been editing these wallpaper configuration files is the Gedit makes a backup of the file. And although this backup file is a hidden file it can still be read by the system because the name has not been changed except to include the tilde character as part of the file name (~). This makes the file a hidden file.

Regards.

---

### Post by Allison_Mann on 2013-08-26
Ok, so it looks like what was causing the problem was a hidden folder of pictures in my root folder that either wallch or wally (another wallpaper changer I was testing out). No idea how they were being pulled to the desktop as they didin't show up when I ran:

dpkg -L ubuntu-wallpapers-precise

Found the offending pictures by running:

gsettings get org.gnome.desktop.background picture-uri 

and deleted the directory.

---

