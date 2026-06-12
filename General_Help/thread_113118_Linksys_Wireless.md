---
title: "Linksys Wireless"
date: 2006-01-05
forum: General Help
---

### Post by Tmyers on 2006-01-05
Recently, I removed ubuntu so that I could repartition the harddrive through the windows installer. I installed windows on one partition and reinstalled ubuntu on another. The first time around, setting my wireless internet up was pretty simple (I have a linksys B Wireless USB Adapter). I ran the ndiswrapper commands and everything just worked. It's being a bit more difficult this time.

The problem is I cant remember exactly how I set it up the first time. What Ive been tying to do is:

1. Put the disk that came with the adapter in the computer
2. Install ndis(wrapper)-utils
3. I copied the drivers folder onto my computer
4. I found all the .inf files and ran "sudo ndiswrapper -i "location to files"
5. Then I went into the networking menu and typed in some things

-network name: wlan
-Key type: not so sure what to select (ive tried both settings)
-config: DHCP

I left the rest blank (this is what i did the first time and it all worked)

Am I missing any steps? Doing anything wrong? I don't even remember having to install ndis-utils the before the reinstallation.

***I have been able to set it up on windows xp, so it's not the drivers/device**

---

### Post by Zelut on 2006-01-05
at first glance it looks like you installed the driver but didn't add it to the kernel modules.

sudo modprobe ndiswrapper

...then you should be able to do your configuration in network-admin.

---

