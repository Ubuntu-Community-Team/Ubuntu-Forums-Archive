---
title: "Ubuntu on Active Directory"
date: 2009-05-27
forum: Desktop Environments
---

### Post by horned0wl on 2009-05-27
Hi All!!  :)

I'm in need of a suggestion or two...  Using a package called "likewise-open," I've gotten an Ubuntu (8.10) workstation to join a Windows 2003-based domain via Active Directory.  Since the hook-up, I've had several folk test it by logging-into their own Active Directory accounts on the Ubuntu machine -- all successfully. :p

My problem is functionality once connected to the domain.  I can still log into the local machine, and I have a default setup in its local /home folder (common wallpaper, all the apps common users on this domain need to access) that I'd like to have become the default /home folder  for anyone logging onto the domain through this Ubuntu box.  I've done it in Windows, but am unsure how to do it in Debian/Ubuntu.  Is there a "default user" or "all users" capability in Debian/Ubuntu?  If so, any suggestions on how to set it up?

Any help appreciated.  Thanks in advance...


Cheers;
Ed

---

### Post by snotplop on 2009-10-29
I'm surprised nobody has answered this one yet.

Let's see if I understand your request correctly....:


You should try to make use of /etc/skel

When a new user is logged in for the first time Gnome(?) checks this directory and copies the entire contents to the new user's home folder.

You can include anything you like from files to the hidden xml-based Gconf files that live in ~/.gconf
The Gconf files handle all the desktop customizations such as wallpaper, panel options and file-associations.

It's better to have separate home folders for each user rather than one massive shared home folder in terms of support and general usability.

---

