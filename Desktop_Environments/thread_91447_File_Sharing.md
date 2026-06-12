---
title: "File Sharing"
date: 2005-11-17
forum: Desktop Environments
---

### Post by UbunuAndrew on 2005-11-17
I'm going keep myself from going ahead and beating around the bush with this one. I download things and have an addiction to it. Generally you want help with addictions.. I do - what is the recommended system to use for a downloader. I use this UbuntuBitTorrent Client, and it just throws errors, so I want to go another route.

---

### Post by earobinson on 2005-11-17
UbuntuBitTorrent = gnome-btdownload (the stock bit torrent dler)

what errors is it throwing maybe we can help you with that!

---

### Post by Ptero-4 on 2005-11-17
aMule is also good. Just stay away from the illegal content that sometimes appear among the search results.

---

### Post by Hairy_Palms on 2005-11-17
gnome-btdownload is a frontend for bittorrent 3.4, i always download and install the latest 4.x version from [www.bittorrent.com](www.bittorrent.com)

---

### Post by taurus on 2005-11-17
Azureus is also another option for bittorent stuff...

---

### Post by UbunuAndrew on 2005-11-17
When using the gnome-btdownload it doesn't matter what file I attempt to use, it give me the error that - invalid literal for long(): i1el43. At this point in time, I haven't attempted to save it to the hard drive, and then open it opposed to opening up through what I suppose is /tmp/ automatically. I'll let you know if that works, otherwise if you've had this issue before maybe you can update me.

Also, Hairy_Palms. I'm very new to Linux and as a desktop user - I am rather clueless on how to install the newer version.

---

### Post by UbunuAndrew on 2005-11-17
UPDATE: Even after saving it to the hard drive, there was no change in the issue. Also, I've tried Azureus, but I get so lost. I've installed Limewire, but when I click the menu button for it, it doesn't run.

---

### Post by Hairy_Palms on 2005-11-17
i assume you have java installed
then to install limewire go to 
[http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)
and download the one that says "Other" its a .zip files, then extract it anywhere and go into the folder and double click "runlime.sh"

to install bittorrent, go to ww.bittorrent.com and download the debian package which is 2nd from the top in the list, then open a terminal where you downloaded it and type 
sudo dpkg-i bittorrent4.04.linux_i686-2_all.deb
u might need python2.3 which is available in synaptic
then its installed and bittorrent should run.

---

### Post by UbunuAndrew on 2005-11-17
When trying to run dpkg I got this any idea on this error? :

andrew@24-52-115-97:~$ sudo dpkg -i bittorrent4.04.linux_i686-2_all.deb
Password:
dpkg: error processing bittorrent4.04.linux_i686-2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bittorrent4.04.linux_i686-2_all.deb
andrew@24-52-115-97:~$

---

### Post by UbunuAndrew on 2005-11-17
I figured it out. A missing "." - I now have BitTorrent working now. Thanks.

---

### Post by earobinson on 2005-11-17
missing "." can you explain? (I would like to learn something from this 2)

---

### Post by UbunuAndrew on 2005-11-17
Yes, sorry.

sudo dpkg -i bittorrent4.04.linux_i686-2_all.deb

Should be

sudo dpkg -i bittorrent4.0.4.linux_i686-2_all.deb

---

### Post by bored2k on 2005-11-17
Discussed. Please use the search tool next time.
[http://www.ubuntuforums.org/showthread.php?t=87795&highlight=p2p+bittorrent](http://www.ubuntuforums.org/showthread.php?t=87795&highlight=p2p+bittorrent)

---

