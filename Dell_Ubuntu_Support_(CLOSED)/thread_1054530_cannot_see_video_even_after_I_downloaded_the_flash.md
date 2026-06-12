---
title: "cannot see video even after I downloaded the flash player"
date: 2009-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lencast on 2009-01-29
can anyone help me with the problem I am having with trying to watch videos that require the flash player.  It downloads it but it doesn't work.  
All   I see is a gray circle with a arrow inside, and when I click on it, the whole area becomes a white space.

Please help.  Thanks:(

---

### Post by Benedolt on 2009-02-21
lencast,

you have the wrong flash plugin installed. That should be easily fixable. Open the "Synaptic Package Manager" by going to 'System'>'Administration'>'Synaptic'
Then make sure the packages 'swfdec-gnome' and 'swfdec-mozilla' are not installed. For that just look for them in the list of all packages, right click and select 'remove'.
Now look for the package 'flashplugin-nonfree' and install that. Now click on 'apply' wait for the installation to finish, restart your Web Browser and you should be all set.

Good luck,
Benedolt

---

### Post by skunkbad on 2009-02-21
You could also go to the Adobe website, and download their .deb for Ubuntu. Once downloaded, simply click on it to do the install.

---

