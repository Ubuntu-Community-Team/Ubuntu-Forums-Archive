---
title: "Firefox problems"
date: 2006-06-08
forum: Desktop Environments
---

### Post by bsell on 2006-06-08
While surfing the web, I came across a site requiring a Flash plug-in for Firefox. In my brief, two month honeymoon with Linux, I've always loaded Flash plug-ins through a package manager. Out of curiosity, I decided to see if I could load the Flash plug-in  through Firefox. After I accepted Macromedia's terms, I downloaded the plug-in and the Flash worked. 

When I booted Ubuntu this evening, I had to fix 3 corrupt files before I could load them and start Gnome. After getting into the desktop and opening Firefox, I noticed my customization  was gone. The theme had reverted to default. The search toolbar did not have any search engines and I couldn't add any. My live bookmarks were there, but I could not add any more bookmarks. To further add insult to injury, Firefox won't let me auto login to any forums. I have to type my username and password each time I open an new instance of Firefox and go to any haunt that requires me to log in.

Any suggestions on how to fix this without a complete reinstall of the Ubuntu desktop? If I do reinstall can I save my docs and files without burning a disc?

---

### Post by jgcamp99 on 2006-06-08
Re-enable Root to login under gnome so you can access and actually copy files to folders, a manual install of Flash 7 is as simple as copying 2 files to:

/usr/lib/firefox/plugins

The 2 files are:

flashplayer.xpt and liflashplayer.so and these are in the tarball that you download from Macromedia.

My only complaint about Ubuntu, it's too secure out of the box. The Root account exists but is disabled. The NTFS partitions don't mount like they do for other Linux distros (that's been covered by other threads). Outside of that, Ubuntu is almost orgasmic for a free OS and applications.

---

### Post by aysiu on 2006-06-09
It sounds as if you might have installed the Flash plugin to your local plugins folder instead of the global one and somehow inadvertantly changed the permissions on your ~/.mozilla folder.

Can you post the output of the following commands? ```
cd
ls -al
``` I'm curious in particular about the ownership and permissions on the /home/bsell/.mozilla folder.

---

### Post by bsell on 2006-06-09
[QUOTE=aysiu]It sounds as if you might have installed the Flash plugin to your local plugins folder instead of the global one and somehow inadvertantly changed the permissions on your ~/.mozilla folder.

Can you post the output of the following commands? ```
cd
ls -al
``` I'm curious in particular about the ownership and permissions on the /home/bsell/.mozilla folder.[/QUOTE]
 
Sure can. 
> 
total 156
drwxr-xr-x 23 brian brian 4096 2006-06-09 07:06 .
drwxr-xr-x  3 root  root  4096 2006-06-05 20:47 ..
-rw-r--r--  1 brian brian  288 2006-06-07 16:35 .audacity
-rw-------  1 brian brian  599 2006-06-08 22:55 .bash_history
-rw-r--r--  1 brian brian  220 2006-06-05 20:47 .bash_logout
-rw-r--r--  1 brian brian  414 2006-06-05 20:47 .bash_profile
-rw-r--r--  1 brian brian 2227 2006-06-05 20:47 .bashrc
drwxr-xr-x  2 brian brian 4096 2006-06-08 22:56 Desktop
-rw-------  1 brian brian   26 2006-06-06 00:55 .dmrc
-rw-------  1 brian brian   16 2006-06-06 00:55 .esd_auth
drwxr-xr-x  8 brian brian 4096 2006-06-08 22:02 .evolution
lrwxrwxrwx  1 brian brian   26 2006-06-05 20:47 Examples -> /usr/share/example-content
drwx------  5 brian brian 4096 2006-06-09 07:06 .gconf
drwx------  2 brian brian 4096 2006-06-09 07:20 .gconfd
drwxr-xr-x 21 brian brian 4096 2006-06-08 19:43 .gimp-2.2
-rw-r-----  1 brian brian    0 2006-06-08 22:00 .gksu.lock
drwxr-xr-x  3 brian brian 4096 2006-06-08 22:14 .gnome
drwx------ 15 brian brian 4096 2006-06-08 22:57 .gnome2
drwx------  2 brian brian 4096 2006-06-05 21:00 .gnome2_private
drwxr-xr-x  2 brian brian 4096 2006-06-06 00:55 .gstreamer-0.10
-rw-r--r--  1 brian brian   87 2006-06-06 00:55 .gtkrc-1.2-gnome2
-rw-------  1 brian brian  644 2006-06-09 07:06 .ICEauthority
drwx------  3 brian brian 4096 2006-06-06 00:55 .metacity
drwx------  4 brian brian 4096 2006-06-08 20:24 .mozilla
drwxr-xr-x  3 brian brian 4096 2006-06-08 20:41 Music
drwxr-xr-x  3 brian brian 4096 2006-06-06 00:55 .nautilus
drwx------  3 brian brian 4096 2006-06-08 21:44 .openoffice.org2
drwxr-xr-x  2 brian brian 4096 2006-06-06 19:27 Pictures
-rw-------  1 brian brian 5024 2006-06-08 23:33 .recently-used
drwxrwx---  3 brian brian 4096 2006-06-06 19:44 .sane
drwxr-xr-x  2 brian brian 4096 2006-06-08 21:50 .serpentine
-rw-r--r--  1 brian brian 8799 2006-06-08 19:31 Space Donkey.odt
-rw-r--r--  1 brian brian    0 2006-06-06 00:55 .sudo_as_admin_successful
drwx------  4 brian brian 4096 2006-06-05 23:47 .thumbnails
drwx------  2 brian brian 4096 2006-06-08 21:51 .Trash
drwx------  2 brian brian 4096 2006-06-06 00:55 .update-notifier
drwxr-xr-x  2 brian brian 4096 2006-06-08 18:50 Wallpapers
-rw-------  1 brian brian  118 2006-06-09 07:06 .Xauthority
-rw-r--r--  1 brian brian 1127 2006-06-09 07:16 .xsession-errors


BTW, can you provide a link to that will allow to read and write to the Linux partitions from Windows?

---

### Post by aysiu on 2006-06-09
Well, assuming your username is *brian*, the permissions look good on the *.mozilla* directory. Do you know if you have read-write-execute permissions on all the subfolders, too? For example, the /home/brian/.mozilla/firefox/*gobbledygook*.default/extensions folder?

You could always try [a fresh Firefox profile](http://www.ubuntuforums.org/showthread.php?t=103930) and see how that does.

And the link you're looking for is [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by bsell on 2006-06-09
[QUOTE=aysiu]Well, assuming your username is *brian*, the permissions look good on the *.mozilla* directory. Do you know if you have read-write-execute permissions on all the subfolders, too? For example, the /home/brian/.mozilla/firefox/*gobbledygook*.default/extensions folder?

You could always try [a fresh Firefox profile](http://www.ubuntuforums.org/showthread.php?t=103930) and see how that does.

And the link you're looking for is [http://www.fs-driver.org](http://www.fs-driver.org)[/QUOTE]

I tried a fresh profile, but I still had problems. I even tried the script nanotube wrote to update Firefox. Firefox closed each time I tried to click on it. Firefox also closed when I tried to check some of my preferences. I did a wget for the latest 1.5.0.4 from the deb repos and this helped. I could add to my bookmarks and auto login to the Ubuntu forums, but couldn't add search engines and still had the problem with the mysterious closing issue on some links. 

Instead of spending several hours hunting down the problem, it was easier to do a fresh install. I only had a few documents to save since I had only recently installed Ubuntu a few days ago. It took less than an hour to get everything in working order and get a Firefox update to the latest version. 

Thanks for the link. I want pull files off of my Linux partitions to save them in Windows. I have more space on that drive. Is there any way I can read and write to my master drive, which has Windows XP, from Ubuntu, which is on my slave drive?

---

### Post by aysiu on 2006-06-09
You can read from Windows XP, but if it's NTFS, you can't write to it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by FredB on 2006-06-10
> **jgcamp99]Re-enable Root to login under gnome so you can access and actually copy files to folders, a manual install of Flash 7 is as simple as copying 2 files to:[/QUOTE]

If you want to live dangerously  said:**
> 
/usr/lib/firefox/plugins

The 2 files are:

flashplayer.xpt and liflashplayer.so and these are in the tarball that you download from Macromedia.

You can also - in the terminal - go to your .mozilla/firefox directory, create a plugin directory and copy these two files. OK, it will be a single user only answer, but far less dangerous than enabling root account.

> 
My only complaint about Ubuntu, it's too secure out of the box. The Root account exists


Too secure ? :p 

> 
 but is disabled. The NTFS partitions don't mount like they do for other Linux distros (that's been covered by other threads). Outside of that, Ubuntu is almost orgasmic for a free OS and applications.

Having root access account is a security basis. Using sudo in terminal with midnight commander (a total commander in text mode clone look-alike) is less dangerous and as powerful.

But as we say in french : *everybody see noon at its door*.

---

