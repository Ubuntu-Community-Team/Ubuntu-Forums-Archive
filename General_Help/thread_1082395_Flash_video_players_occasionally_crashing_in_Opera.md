---
title: "Flash video players occasionally crashing in Opera 9.63"
date: 2009-02-27
forum: General Help
---

### Post by pokeyThePenguin on 2009-02-27
Ubuntu 8.04
GNOME 2.22.3
Opera 9.63
I have flashplugin-nonfree and libflashsupport installed.

I'll load a page that has a flash player. The flash player shows up, but then disappears. Sometimes scrolling down the page and then scrolling back up gets all the flash to appear.

Or, I'm in the middle of watching a video, and the player just disappears. Reloading the page helps get all the flash working again.

What can I do to get flash working consistently in Opera?

---

### Post by Lunx on 2009-02-27
Does the path to the plugin show up in Opera?

**Help --> About Opera --> Paths**

What version of Flash? Many sites now need V10

---

### Post by Lunx on 2009-02-27
Should show up as 

/usr/lib/flashplugin-nonfree

---

### Post by pokeyThePenguin on 2009-02-27
Yep, it shows up:
Plug-in path
/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/flashplugin-nonfree

I just uninstalled flashplugin-nonfree and installed adobe-flashplugin. I had V9, and now I have V10. :)

I'll let you know if my problems still persist.

Thanks for the help.

---

### Post by Lunx on 2009-02-27
No worries, I had exactly same problem when I first installed and that solved it for me (I'm using same version of Opera)

---

### Post by pl_jarek on 2009-03-04
I found this solution:

[I]Now you need to install Flash9 from here

Now you need to extract this file using the following comand

sudo tar xzvf install_flash_player_9_linux.tar.gz

Now you need to go in to the install_flash_player_9_linux directory

cd install_flash_player_9_linux/

sudo cp libflashplayer.so /usr/lib/opera/plugins

sudo cp flashplayer.xpt /usr/lib/opera/plugins[/I]

and it works :D (opera 9.64 + ubuntu 8.04 + flahplayer)

---

### Post by pl_jarek on 2009-03-04
link below:

[http://www.filewatcher.com/m/install_flash_player_9_linux.tar.gz.2608602.0.0.html](http://www.filewatcher.com/m/install_flash_player_9_linux.tar.gz.2608602.0.0.html)

I used this one:

[ftp://ftp.urc.ac.ru/pub/OS/FreeBSD/distfiles/flashplugin/9.0r48/install_flash_player_9_linux.tar.gz](ftp://ftp.urc.ac.ru/pub/OS/FreeBSD/distfiles/flashplugin/9.0r48/install_flash_player_9_linux.tar.gz)

---

### Post by Flywaver on 2009-03-04
thanks pl_jarek !!

But since I removed flashplugin-free it no longer works in FF...how do we go ahead and manually install the files for ff?

Thanks!

---

### Post by pl_jarek on 2009-03-05
At the beginning I made it directly from adobe site, when the www browser asked me to install flash.

---

### Post by pl_jarek on 2009-03-05
Then I didn't know that this instalation not support Opera but ff. :D

---

