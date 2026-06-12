---
title: "Saving files to ubuntu"
date: 2005-11-30
forum: Desktop Environments
---

### Post by penguinman007 on 2005-11-30
Needed to get rid of brown background.
Downloded image to filesystem usr/share
image was not there.

I need access to all folders, all drives and everything.

I can only download to the desktop.
When I put things in the recycle bin, they are gone forever.
Opening the recycling bin does not display what I put there.

I like having a powerful, free, awsome looking linux.
But I want root access to everything.
now.

---

### Post by matthewv on 2005-11-30
I think its possible to enable root access to everything, but its definitely not the way to go. You can download to everywhere in your home directory, without trouble. If you need a place accessible by all users, create a shared directory within your home dir, or something like that, and allow all users to r/w.

---

### Post by Sionide on 2005-11-30
as the above post said; you should use your Home directory for storing files..

I have a /home/sionide/wallpapers directory for wallpaper images, for example. Think of it as your "My Documents" folder on Windows, except it also holds a lot of configuration for applications in hidden directories as well.

---

### Post by anil_robo on 2005-11-30
The security of linux is dependent on many components, one of which is the users and root system. It is not advised to keep yourself logged in as root all the times. If you need special privileges, better be a superdoer (use sudo command) instead of root (su). Automatic login of root into GDM is  possible, but not secure. See this: [http://www.ubuntuguide.org/#automaticlogingnome](http://www.ubuntuguide.org/#automaticlogingnome)

---

### Post by aysiu on 2005-11-30
I need access to my money as well.
Fortunately, the bank makes me enter a pin code every time I withdraw money.

Same thing with Ubuntu--enter your password to access important system files and directories.

If you don't want to have a "secure" place to save things, save them where they're *supposed* to go: /home/penguinman007/Desktop

---

