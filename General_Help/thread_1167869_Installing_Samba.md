---
title: "Installing Samba"
date: 2009-05-23
forum: General Help
---

### Post by Lacrimo on 2009-05-23
I have this Ubuntu 9.04 computer here, and I want to able to exchange files between here and a Vista computer downstairs - where the printer is. Both these computers are on my wireless network. When I look in the networks folder, I see the "Windows Network" icon, which produces errors when I try to open it. I wonder if sudo apt-get samba will let me open it without any further work - like sudo apt-get rar - or if I need to configure it or some such.

Thanks for your time.

---

### Post by albinootje on 2009-05-23
> **Lacrimo said:**
> When I look in the networks folder, I see the "Windows Network" icon, which produces errors when I try to open it.

Should work without installing extra software.
You can try this inside nautilus : smb://your_ms-vista_machine/

First click on the icon at the left, see screenshot, and then type in the ip address of your machine.
Please report back if that gives problems too.

---

### Post by coffeecat on 2009-05-23
First, create a folder in your home for a share, right-click on it and enable sharing. This will cause the missing bits of samba to be installed. Log out and in again when prompted, right click on the folder again and make sure sharing has been enabled.

Next, edit smb.conf according to post #24 in this thread:

[http://ubuntuforums.org/showthread.php?t=1135842&highlight=jaunty+share+folder&page=3](http://ubuntuforums.org/showthread.php?t=1135842&highlight=jaunty+share+folder&page=3)

Now check the 3 points in this post (the third needs an edit of /etc/nsswitch.conf):

[http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

I have four computers with Jaunty on my network. Bizarrely, I had to do all of these on one, and some or none of those on the others to get smb shares to work in all directions. Pass. :confused:

Also, it can take several minutes after bootup before the various shares appear as clickable icons in Places > Network.

---

### Post by Lacrimo on 2009-05-23
Thanks for the help. Got it working.

---

