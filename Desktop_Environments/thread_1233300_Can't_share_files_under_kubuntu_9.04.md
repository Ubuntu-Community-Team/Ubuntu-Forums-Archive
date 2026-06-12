---
title: "Can't share files under kubuntu 9.04"
date: 2009-08-06
forum: Desktop Environments
---

### Post by henry83 on 2009-08-06
I have tried to share files in a LAN between two computers under kubuntu 9.04 32 bits with no success when I click on "configure file sharing" nothing happens. Any idea to solve this problem?

---

### Post by Zorael on 2009-08-06
Where is this "configure file sharing" you speak of? The option I have, in **System Settings** -> *Advanced* tab, is named **Samba**. (To get it to show up you need to have the **kdenetwork-filesharing** package installed.)

If it's the same one and you're just running KDE in another language, try the following in a terminal to open it directly. If it doesn't open up on the first try, enter it again. (Omit the dollar-sign **$**)
```
$ kdesudo kcmshell4 kcmsambaconf
```
There's also another, older menu with less settings.
```
$ kdesudo kcmshell4 filesharing
```

---

### Post by henry83 on 2009-08-06
Hi! I ment when I'm inside Dolphin or Konqueror and I right click a folder and there I go to share->configure file sharing then I'm prompted to  run kdesudo kcmshell4 filesharing and then nothing happens... Samba works what I can't do is to access the other computer while both are running kubuntu

---

### Post by warp99 on 2009-08-06
> **henry83 said:**
> Hi! I ment when I'm inside Dolphin or Konqueror and I right click a folder and there I go to share->configure file sharing then I'm prompted to  run kdesudo kcmshell4 filesharing and then nothing happens... Samba works what I can't do is to access the other computer while both are running kubuntu

You can install ssh and use the FISH protocol in KDE to transfer files via Konqueror or Dolphin. This is how I transferred files for years until I switched to Gnome. Here's a guide on how to set this up:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

Once you transfer the public keys on each machine open Konqueror (or Dolphin) and type fish://<ip_addr> in the URL locater. You'll be connected to the user share of the other machine. You can also set up a desktop link doing the exact same thing. Just use fish://<ip_addr> as the URL.

Edit:
You can install a Samba server on one of the machines and access the other with a Samba client with Kubuntu on both machines, but ssh/FISH is much easier and faster once you set it up. Here's a picture of FISH in action:

[http://linuxreviews.org/kde/kde-user-persp/fish.html](http://linuxreviews.org/kde/kde-user-persp/fish.html)

---

### Post by henry83 on 2009-08-07
Thank you friend I have forgotten about fish but I had used it already. Why did you switch to gnome? just being curious.

---

### Post by Zorael on 2009-08-07
As a small note, do make sure you have that **kdenetwork-filesharing** package installed since it actually contains the settings page where you manage samba shares (kcmsambaconf). I had to tag it manually.

---

### Post by warp99 on 2009-08-07
> **henry83 said:**
> Thank you friend I have forgotten about fish but I had used it already. Why did you switch to gnome? just being curious.

I switched to Gnome because KDE 4.2 compositing wasn't as good and feature rich as with Compiz-Fusion. I did get Compiz-Fusion to run under 4.2 but it was too unstable with video tearing and crashing on startup. 

Other reasons were that I didn't like the new Amarok 2.0, Kaffeine was missing, and 4.2 didn't have the customization features with desktop panels as with previous KDE versions. 

To make a long story short 3.5.9 was getting long in the tooth while 4.2 didn't offer anything compelling for me to make the switch permanent, so with a "sudo aptitude install ubuntu-desktop" I made the move to Gnome.

---

### Post by schnelle on 2009-08-07
Try this link:

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/](http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/)

Everything explained. There are even pictures for "total newbies" ;)
It helped me btw.

---

