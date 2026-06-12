---
title: "Missing 'Send to Trash' right click option after re-install"
date: 2015-10-15
forum: Desktop Environments
---

### Post by makem2 on 2015-10-15
In my first install of xubuntu I had two right click options in respect of removing files and directories, move to trash or delete.

I used these a number of times so had a few files in the Wastebasket.

I re-installed xubuntu keeping my /home directory in the process.

I now have a Wastebasket Icon as usual but according to it, it is empty. It is not and has several files in it.

When I right click to remove a file I now only see the Delete option. Send to Trash is missing.

I made a test file on the Desktop and tried to send it to the Wastebasket:

```

makem@newTOSH:/$ gvfs-trash /home/makem/Desktop/test
makem@newTOSH:/$

```

This worked and the test file was move to the correct Wastebasket directory. The file showed when the Wastebasket icon was selected.

I added a Custom Option in File manager. Name; Send to Wastebasket, Description; Send Selected to Wastebasket, Command; gvfs-trash.
I selected all of the Appearance Conditions.

However, I have no means of instigating that command as it does not appear in the right click context menu.

Any guidance gratefully accepted.

Edit: The Move to Wastebasket option appears upon right click on files/directories which are in File Manager but not when items on the Desktop are selected.

So it appears only files on the Desktop cause this problem.

If I Delete from the Desktop item are sent to the Wastebasket - no warning. If I delete from File Manager I get a warning and files are permanently deleted. Is this the normal action?

---

### Post by ajgreeny on 2015-10-15
Which version of Xubuntu running which version of xfce?

I think previous versions of xfce to the one I now use (4.12 from the ppa at [http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu](http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu)) did not give the Delete option from the Desktop but did from the file manager, just as you are seeing things now.

XFCE 4.12 does give you both options, ie **Delete** and **Move to Trash**, or it does in my Xubuntu 14.04.

---

### Post by makem2 on 2015-10-15
I don't know how to find the xfce version

Trusty 14.04 LTS

From 
[h=1][SIZE=3]Index of /sites/cdimage.ubuntu.com/cdimage/xubuntu/releases/14.04/release/[/SIZE][/h][URL="http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/xubuntu/releases/14.04/release/xubuntu-14.04-desktop-amd64.iso"]xubuntu-14.04-desktop-amd64.iso

[/URL]

---

### Post by Bashing-om on 2015-10-15
makem2; Hello;

Activate a terminal and execute terminal commands:
```

xfce4-session --version
lsb_release -a

```
And paste back between code tags. 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]and these tales will be told
[/INDENT][/INDENT]

---

### Post by makem2 on 2015-10-16
Thank you for that guidance.

```

makem@newTOSH:~$ xfce4-session --version
xfce4-session 4.10.1 (Xfce 4.10)

Copyright (c) 2003-2012
    The Xfce development team. All rights reserved.

Please report bugs to <http://bugs.xfce.org/>.
makem@newTOSH:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    

```

Are there other advantages to upgrading manually to the same xfce version as you ie. keep to the latest version?

I thought the update system looked after that so I must find out more about the subject to see how to deal with it.

Edit. I find that Xfce 4.12 was released on 28th February so have the details. Also the release of xubuntu 15.04 which I will not update just yet.

---

### Post by ajgreeny on 2015-10-16
I have been using xfce 4.12 for several months now with no problems at that I have noticed.

The ppa repositories I spoke of are a way to sometimes get more recent versions of packages than are available in the standard repos for a *ubuntu version, or to get packages that are not available at all for Ubuntu and I use a few for applications such as Libreoffice 5.0.2.2, and of course, xfce 4.12.

Go to [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12?field.series_filter=trusty](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12?field.series_filter=trusty) for instructions on enabling the ppa if you want to try it; I believe the risk is extremely small and you can always revert to the standard repos later if you have problems, which I don't think you will.

---

### Post by makem2 on 2015-10-16
Thank you, I will try it later when I am more confident.

My current project is Custom Actions and I struggle with opening Firefox with a right click on the Desktop although I can achieve it from a Directory :frown:

---

