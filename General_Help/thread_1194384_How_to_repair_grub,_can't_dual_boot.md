---
title: "How to repair grub, can't dual boot"
date: 2009-06-22
forum: General Help
---

### Post by nonzer0 on 2009-06-22
I know there a ton of these posts and I've been able to fix this many times, but I don't know what to do now.  I just built a new PC and I partitioned my hdd to boot ubuntu, xp, and vista.  After installing vista, I used super grub loader to restore the grub.  

Now my grub lists my new ubuntu, my 2 old ubuntu installs, and other operating systems.  But when I click on other operating systems, I get error 11, unrecognized string. 

I can get windows to work by going into repair console, but then I can't boot ubuntu.

Can someone explain how to delete the unneeded os's from the grub list and how to get windows listed under the other operating systems option in grub

---

### Post by JeffersonX on 2009-06-22
Did you install Ubuntu after xp and vista?

If you done this, I recomend you to repair with this command:

sudo grub-install --root-directory=/mnt /dev/sdY

where /dev/sdy is your partition where Ubuntu is installed.

To use this command, you have to use your live cd.

Please, verify if your /boot/grub/menu.lst has been configured correctly.

---

### Post by nonzer0 on 2009-06-22
I installed Ubuntu first.  I don't know why I did that, since installing xp or vista after ubuntu always leads to problems for me.  Can I delete the grub completely, and then rebuild it?  Will that remove the other two distros listed in the grub?  I have little to know idea how grub and mbr work.

---

### Post by JeffersonX on 2009-06-22
I think it was an error in your /boot/grub/menu.lst. That's why your Grub shows you others distros.

I found this how to on Ubuntu Documentation. It may help you.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ajgreeny on 2009-06-22
You say you "click on other operating systems" is that actually the line you click on or does it say "Windows" or something similar.

It sounds rather as though you sre not clicking on the kernel line for windows.  Your /boot/grub/menu.lst should have a stanza something like
```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```for windows. If it does not exist try adding it, but make sure your partition info, ie, the (hd0,0) on mine, is correct for your system.

---

### Post by ahndoruuu on 2009-06-22
You just have to make sure the entries in GRUB are pointing to the actual locations of your OSes.  You can try editing your "/boot/grub/menu.lst" file manually.

To find out where your OSes are located you can use this command
```
sudo fdisk -l
```

Also, all GRUB entries are listed in /boot/grub/menu.lst , feel free to delete unneeded entries for a tidier menu ;)

---

### Post by nonzer0 on 2009-06-23
> **JeffersonX said:**
> I think it was an error in your /boot/grub/menu.lst. That's why your Grub shows you others distros.

I found this how to on Ubuntu Documentation. It may help you.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


That guide worked very well.  I appreciate it.  Just wish I understood what all that stuff in the grub file is.

---

### Post by bodhi.zazen on 2009-06-23
> **nonzer0 said:**
> That guide worked very well.  I appreciate it.  Just wish I understood what all that stuff in the grub file is.

See this page [http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

