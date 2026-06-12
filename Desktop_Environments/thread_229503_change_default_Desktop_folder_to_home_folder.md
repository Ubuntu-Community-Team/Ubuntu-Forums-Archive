---
title: "change default Desktop folder to home folder"
date: 2006-08-04
forum: Desktop Environments
---

### Post by desimo on 2006-08-04
Apologies if this has been asked before, but I was having trouble finding it...

Is there a way for me to make it so that my desktop shows the contents of my home folder?

For example, if I am logged in as "user", I would like the desktop to show the contents of /home/user instead of /home/user/Desktop

I would like to delete (or ignore) the actual /home/user/Desktop folders on my system. 

TIA,
desimo

---

### Post by Dubbayoo on 2006-08-04
not sure that's a great idea but this might do it.

rm -rf /home/user/Desktop
ln -sf /home/user/ /home/user/Desktop

---

### Post by aysiu on 2006-08-04
Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Preferences > Desktop_is_home_dir

I wouldn't recommend it, though.

---

### Post by desimo on 2006-08-05
What is the reason that this is not recommended?

---

### Post by desimo on 2006-08-05
Changing the setting in "configuration editor" is exactly what I was looking for: thank you.

desimo

---

### Post by aysiu on 2006-08-05
> **desimo said:**
> What is the reason that this is not recommended?
I can't dig up the reference right now, but I remember reading on the Gnome mailing lists somewhere that it could cause some instability.

---

### Post by talking Llama on 2008-04-16
Hey, just wondering, is there a way of reversing this. I mean that for some reason my desktop thinks it is my home folder, its path is /home/[user] instead of /home/desktop or whateevr it should be. ANy help would be much appreciated?

---

### Post by jpeddicord on 2008-04-16
Reversing:

> **aysiu said:**
> Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Preferences > Desktop_is_home_dir

I wouldn't recommend it, though.

Uncheck the checkbox. :)

---

### Post by talking Llama on 2008-04-16
Lols, I checked the box and it's unchecked its just for some reason my Desktop folder went missing and now all my user files from /home/[user] are being displayed on the desktop? I've read about this problem some other places but it says something about editing some config file somewhere? Any help?

---

### Post by Riel on 2008-05-07
Hello,

i sucessfully changed the ~/.config/user-dirs.dirs to take my own dirs for desktop.

But, when restarting pc / logging out/in, it all resets to default /home/User/xxxx

How can I fix that? Permissions are

-rw------- 1 riel riel 1091 2008-05-07 18:42 user-dirs.dirs

---

