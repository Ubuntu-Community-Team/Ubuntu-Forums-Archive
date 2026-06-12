---
title: "Quick HowTo: Create an &quot;Open as Administrator&quot; icon on the Desktop"
date: 2009-02-06
forum: General Help
---

### Post by mb_webguy on 2009-02-06
I've been using this for nearly as long as I've been using Gnome on Linux, and it just occurred to me that others might find it useful...

The goal:  To have an icon on the desktop that allows you to open any file or folder with superuser (i.e. root) privileges using its associated application.  (Granted, if you're using Nautilus, you can simply install the nautilus-gksu package to give you an "Open as administrator" option in the context menu, but if you're using Thunar or another file manager, this desktop icon can come in handy.)

This is actually very simple.  Right-click on the desktop and select "Create Launcher" from the context menu.  For the Name, type "Open as Administrator" (or whatever you want to call it).  For the Command, type (or paste) the following command:```
gksudo "gvfs-open %u"
```For the Comment, put anything you like.  Change the icon if you want, then click "Ok".

That's it.  Now all you have to do to open a file or folder as root is to drag that file or folder's icon from your file manager and drop it on that icon.  Dropping a text file on the icon will open the file using the equivalent of "gksu gedit *filename*" (if gedit is your default text editor), dropping a folder on the icon will open the folder using the equivalent of "gksu nautilus *folder*" (if nautilus is your default file manager), etc.  Enjoy!

---

### Post by scouser73 on 2009-02-06
Great tutorial, typing gksudo nautilus all the time was doing my head in, thanks once again.

---

### Post by demosthenese on 2009-02-06
That's neat, but maybe use xdg-open for other desktop managers.

---

### Post by mb_webguy on 2009-02-06
I've only briefly used KDE and Xcfe, so I'm not familiar with the equivalent to gvfs-open in other desktop environments.  That's why this post is marked as [Ubuntu].  ;)

---

### Post by GreginSJ on 2011-05-05
What a great tip.  Worked for me as promised.  Is there not a way, however, to simply have SuperUser privileges while working in Gnome?  I log in as Administrator, but I still can't move files from one directory to another or create a file in gedit and save it - all because the system says I don't have the proper privileges.  Your "Open as Adminstrator" fixes the problem with a drag and drop option (pretty slick), but why isn't there a way just to always have those privileges at my disposal after log in?  I'm using 10.04 LTS Lucid Lynx.  Thx

---

### Post by compmodder26 on 2011-05-05
> **GreginSJ said:**
> What a great tip.  Worked for me as promised.  Is there not a way, however, to simply have SuperUser privileges while working in Gnome?  I log in as Administrator, but I still can't move files from one directory to another or create a file in gedit and save it - all because the system says I don't have the proper privileges.  Your "Open as Adminstrator" fixes the problem with a drag and drop option (pretty slick), but why isn't there a way just to always have those privileges at my disposal after log in?  I'm using 10.04 LTS Lucid Lynx.  Thx

Your "administrator" account is still a regular user account.  The only difference is the account can use "sudo" to gain root privileges.  The idea of running always as root is a bad idea.  Bad things can happen.  Running as a normal user who occasionally gets elevated privileges greatly reduces the risk that something will get messed up.

---

