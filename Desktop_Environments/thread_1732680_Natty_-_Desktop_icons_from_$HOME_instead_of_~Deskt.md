---
title: "Natty - Desktop icons from $HOME instead of ~/Desktop"
date: 2011-04-18
forum: Desktop Environments
---

### Post by PhDLinux on 2011-04-18
I used the command "update-manager -d" to put Natty Beta 2 on my Acer Aspire One netbook. It worked perfectly, but took about 7 hours because the SSD is so slow. The upgrade replaces the Netbook Remix of Ubuntu 10.10.

Now my desktop is full of icons that weren't there before. They are the files and folders in my home directory. Until yesterday, my desktop icons showed the contents of the subdirectory $HOME/Desktop instead. How can I restore the former behaviour?

The desktop icons are being provided by Nautilus. I know this because I can drill down into the Nautilus options using gconf-editor and un-check the box that makes Nautilus manage the desktop. This makes all the icons go away. So I know how to get (1) lots of icons [the wrong ones] or (2) no icons at all. I'd like an elegant clean way to achieve (3) just a few icons [the right ones]. Suggestions?

[My idea of "elegant": some way to inform Nautilus about which directory to look in for the purpose of generating icons for the desktop. My friend Google has been less helpful than usual on this quest.]

Thanks!

---

### Post by mcduck on 2011-04-18
Make sure you have a directory called "Desktop" inside your home directory. Then open gconf-editor and make sure *apps/nautilus/preferences/desktop_is_home_dir* -key is disabled. And finally make sure that the *~/.config/user-dirs.dirs* -file has the following line in it:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```
(if this line isn't there or has wrong value you'll have to log out and back again before the change takes effect)

---

### Post by PhDLinux on 2011-04-18
Mcduck, your superb, elegant, on-topic, content-packed response solved my problem within an hour of uploading my question. Impressive. Thanks!!!

---

