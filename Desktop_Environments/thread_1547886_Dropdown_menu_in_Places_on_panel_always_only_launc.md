---
title: "Dropdown menu in Places on panel always only launches Banshee."
date: 2010-08-07
forum: Desktop Environments
---

### Post by crossstick on 2010-08-07
Ubuntu 10.04 (Lucid), GNOME 2.30.2. After some time of correct operation, my dropdown menu from "Places" in the GNOME Panel has gone wrong.

 If I click Places and then click on any of the dropdown shown, Home Folder, Desktop, Documents, Music, Pictures, Videos, Downloads, before the horizontal line separator, Banshee launches. Those after the separator, Computer, Floppy and my Hard Drives, launch correctly.

 I have tried restoring the Panel to its original setting with no luck.

Is there a way out of this please?

Thanks

---

### Post by ajgreeny on 2010-08-07
Just out of interest try adding the **main menu** to your panel and see if the behaviour is the same.

Perhaps worth renamimg the **~/.gconf/apps/panel** and **~/.config/menus** folders and restarting x, or rebooting.

---

### Post by crossstick on 2010-08-08
No, no luck with that sorry although adding Main Menu works properly as did System Monitor when I also added that.

I've removed Banshee, all works OK.
 Restarted and re-installed Banshee - fault is back.
If I navigate via Computer to my Documents folder and make a link to Documents and then place that link onto my desktop, then clicking on it launches Documents OK.
If I place that link onto the Panel then Banshee launches.

I'm more or less resigned to adding shortcuts for Docs, Pics, Music and Downloads to my Desktop and living with it.

Thanks.

---

### Post by Balthazar_Droid on 2011-01-01
Subscribing. I have the same problem. I'm curious to see if you fix this.

---

### Post by waspbr on 2011-01-04
same here, whenever I click the Places menu it launches banshee.

---

### Post by sokekoke on 2011-01-10
Same problem... very strange !! hehe

---

### Post by fixor on 2011-01-22
Hi,

I'm far from being an ubuntu pro so use my advice with caution. I had the same issue though and I found  [URL="http://ubuntuforums.org/archive/index.php/t-1151325.html"]this thread.
[/URL]
One of the users posted a very elaborate solution which, lacking the skills, I did not follow thoroughly. What worked for me was simply editing this file

 .local/share/applications/mimeapps.list

and changing an entry with banshee process that was run by places menu (banshee-1 in my case) to this:

inode/directory=nautilus-folder-handler.desktop;

(before the change it stated: inode/directory=banshee.something.something.desktop;)

computer magic!

It would be great if anybody could verify this and maybe write a more specific solution.

good luck anyway,
Wiktor

---

### Post by Krytarik on 2011-01-22
That's completely right, fixor, and specific enough! ;)

---

### Post by Daouuu on 2011-01-22
I have almost the same issue except when I click anywhere between Home Folder and Ubuntu One in the Places menu it brings me to Appearance Preferences/Background.

Any advise on how to return this to normal?  I can't seem to find the file referred to in the previous post.

---

### Post by Krytarik on 2011-01-22
The mentioned path is from the home directory of the user.
And the file must be there. Just enter this in a terminal:
```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by Daouuu on 2011-01-22
Fixed, thanks!

---

### Post by waspbr on 2011-01-31
right on the money, thanks.

---

