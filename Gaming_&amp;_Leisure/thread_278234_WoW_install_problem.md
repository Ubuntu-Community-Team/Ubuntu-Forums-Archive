---
title: "WoW install problem"
date: 2006-10-16
forum: Gaming &amp; Leisure
---

### Post by reazn on 2006-10-16
Hey guys, 

Read the HOWTO on installing wow & wine, install wine and goto run the installer.exe (which i have copied to my hd) and wine gives me a wierd error saying that there is not enough space on the drive.

Not exactly sure if it meens the windows directory which it has made or my actuall hd. Either way, there is plenty of space.

Any Suggestions?

Thanks in advance

---

### Post by Ferrat on 2006-10-16
> **reazn said:**
> Hey guys, 

Read the HOWTO on installing wow & wine, install wine and goto run the installer.exe (which i have copied to my hd) and wine gives me a wierd error saying that there is not enough space on the drive.

Not exactly sure if it meens the windows directory which it has made or my actuall hd. Either way, there is plenty of space.

Any Suggestions?

Thanks in advance

Yes, you are running a new version of wine I guess, they work great to play with but the installer messes up, download wine 0.9.13 and complie and install, then the installer works fine, then after install, install wine 0.9.23 over that =)

---

### Post by reazn on 2006-10-16
> **Ferrat said:**
> Yes, you are running a new version of wine I guess, they work great to play with but the installer messes up, download wine 0.9.13 and complie and install, then the installer works fine, then after install, install wine 0.9.23 over that =)

i'll give it a try when i get home from work, thanks :)

---

### Post by dasuberdog on 2006-10-17
I am having the same problem...

I installed wine using    	
2 Attachment(s) HOWTO: WoW under 6.06 with Wine - NVIDIA/ATI post

"Latest Version = 0.9.22. The patched .deb in the torrent is patched for NVIDIA and ATI, but untested for ATI as I don't have the hardware, so let me know!

WoW will not work with anything under 0.9.16-18 or so, and it is best to install the latest version for all the bugfixes and performance goodness.

The method depends on whether you are using 32 or 64 bit.

32 bit NVIDIA and ATI users:
Download and force-install the patched version:
[http://files.pablasso.com/opensource...22-1_amd64.deb](http://files.pablasso.com/opensource...22-1_amd64.deb)
Code:

sudo dpkg -i --force-architecture wine_0.9.22-1_amd64.deb 
sudo apt-get -f install 
winecfg"

One thing I am doing a little different is that I had a linux partition and a windows partition so linux is installed where windows used to be and I have a fat32 partition that I need to install Wow on which is media/hda5 or D:

---

### Post by hikaricore on 2006-10-17
fyi: your link got trunicated a bit there i belive

---

### Post by dasuberdog on 2006-10-17
doh....  here is the link  [http://www.ubuntuforums.org/showthread.php?t=243336&highlight=wow](http://www.ubuntuforums.org/showthread.php?t=243336&highlight=wow)

---

