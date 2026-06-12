---
title: "Desktop issues"
date: 2009-07-11
forum: Desktop Environments
---

### Post by dans1610 on 2009-07-11
Hi,

I'm having some issues with my desktop. Basically I can't drag anything on to it, can't see any icons on it (even when there are files in the "~/Desktop" directory), and I have no right click context menu either.

However, whenever I open Nautilus in root, I get my desktop back fully functioning (minus the background).  However I discovered that actually it was displaying the root user's Desktop directory, not mine.thing

I thought this may of been a permissions issue, so I looked at the permisions of my Desktop directory, and I (dan) was the owner and "group".

I've also tried reinstalling nautilus, to no avail either.

Since I'm new to Linux and Ubuntu, I'm not really sure what the problem is, so any help would be much appreciated.

Thanks for any help in advance,

Dan

---

### Post by ajgreeny on 2009-07-11
I seem to remember hearing about this problem once or twice before and think it was solved by changing a setting in gconf-editor.

Use Alt+F2 to open the run dialog and type **gconf-editor**.  Now go to **apps > nautilus > preferences** and uncheck the box beside **desktop_is_home_directory** if it is selected.  You may need to logout and in again for any changes to show.

If it is not already selected, then I'm afraid I do not have other suggestions.

---

### Post by ccnjim on 2009-07-11
I'm a new user also. What you're describing is what I do on purpose to enable 4 wallpapers. (I uncheck show desktop)

Open conf.editor. go to_** apps>nautilus>prefrences**_ make sure _**show desktop is checked**_.

---

### Post by dans1610 on 2009-07-11
Yeah, I appreciate the help, but home_dir_is_desktop was unchecked and show_desktop was checked unfortunatly.

Thanks for the help anyway, may just have to reinstall.

---

