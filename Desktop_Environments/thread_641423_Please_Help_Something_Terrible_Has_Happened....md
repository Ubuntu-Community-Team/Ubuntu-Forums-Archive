---
title: "Please Help Something Terrible Has Happened..."
date: 2007-12-15
forum: Desktop Environments
---

### Post by lenswipe on 2007-12-15
Hi


as you have probably guessed im in pretty urgent need of help....

i recently tried to install KDE via command line using the following command:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

which i got from [here]("http://www.psychocats.net/ubuntu/kde")

When i try to play a DVD under KDE it just says something about HAL could not be started or something. And when i log into GNOME i just get a black desktop and the same error message. The right click menu has also gone from the desktop so if i right click on the desktop nothing happens....


Please help


PS

I dont mind removing KDE if i have to (i dont think its that great anyway..)

[EDIT] I just removed KDE anyway to see if it would solve the problem

thanks

lensiwpe :p

---

### Post by taurus on 2007-12-15
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by lenswipe on 2007-12-15
> **taurus said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

thanks but i already removed Kubuntu. But i still have no wallpaper or desktop icons and im still getting an error message about HAL and when i try to boot from the live CD i get an error message about GNOME and KDE.

And there are NO icons next to the items on the menu in fact it looks like windows 2000 but for all the wrong reasons....


Im thinking of just formatting the partition with Ubuntu on and going for a clean re-install.

Can anyone tell me how to format the ubuntu partition WITHOUT harming vista and delete the ubuntu partion so i can start from the beinging.


Thanks

---

### Post by taurus on 2007-12-15
If you want to reinstall, just use the Manual option from the LiveCD when you get to the partition screen.  Tell the installer to use what partition for / and which for swap.  Don't forget to format the partitions so you would have a clean Gutsy again.

---

### Post by lenswipe on 2007-12-15
> **taurus said:**
> If you want to reinstall, just use the Manual option from the LiveCD when you get to the partition screen.  Tell the installer to use what partition for / and which for swap.  Don't forget to format the partitions so you would have a clean Gutsy again.

Hmmm How do i format partitions??


Just check the box in the format column?


Thanks :)

---

### Post by taurus on 2007-12-15
Yes.

---

### Post by lenswipe on 2007-12-15
> **taurus said:**
> Yes.

ok thank you very much :):):)


i would +rep you but there isnt a reping system :(

---

### Post by lenswipe on 2007-12-15
Hi there

I had problems with Ubuntu and i posted here asking for help and had my post answered. The person who answered my post said i needed to re-install Ubuntu. When i put the Live CD in and tried to install it i got the following message:

[IMG]http://i221.photobucket.com/albums/dd12/lenswipe/Screenshot.png[/IMG]

---

### Post by jken146 on 2007-12-15
You need to choose a partition for / and label it as / using "edit partition" on that screen.

Plan your partitions carefully and if you're scared you'll make a mistake, back up first!

---

### Post by sirdilznik on 2007-12-15
You need to have a root partition defined in order to have a system (not to be confused with the "root" folder which is the root user's home folder).  This root partition is basically your main system.  Think of the root partition as the tree trunk of the tree and all other folders or partitions (in the Linux install) stemming from it.  Thus the root partition will be mounted at mount point ```
/
```.  You don't want to touch your ntfs partitions, those are your vista partitions.  Swap is like a page file(or swap file) in windows.  That leaves only one partition according to your layout```
/dev/sda3
```Change the mount point of that partition to ```
/
```

Edit: You know that /dev/sda3 is a Linux partition because it is of type ext3.  this is one of many filesystems available in Linux (and the default).  Partitions of type fat16 or fat32 or vfat or ntfs are Windows type filesystems.  You want to leave those alone and NOT reformat those.  You only need to reformat the ext3 partition (/dev/sda3)

---

### Post by lenswipe on 2007-12-15
> **sirdilznik said:**
> You need to have a root partition defined in order to have a system (not to be confused with the "root" folder which is the root user's home folder).  This root partition is basically your main system.  Think of the root partition as the tree trunk of the tree and all other folders or partitions (in the Linux install) stemming from it.  Thus the root partition will be mounted at mount point ```
/
```.  You don't want to touch your ntfs partitions, those are your vista partitions.  Swap is like a page file(or swap file) in windows.  That leaves only one partition according to your layout```
/dev/sda3
```Change the mount point of that partition to ```
/
```

Edit: You know that /dev/sda3 is a Linux partition because it is of type ext3.  this is one of many filesystems available in Linux (and the default).  Partitions of type fat16 or fat32 or vfat or ntfs are Windows type filesystems.  You want to leave those alone and NOT reformat those.  You only need to reformat the ext3 partition (/dev/sda3)

i would much prefer it if i could format the ubuntu partitions so they were empty, delete them and go back to a hard drive with windows vista and free space. Then i could start over (WITHOUT KDE THIS TIME)

Is there a way to do this??

Please help

---

### Post by schauerlich on 2007-12-15
> **lenswipe said:**
> i would much prefer it if i could format the ubuntu partitions so they were empty, delete them and go back to a hard drive with windows vista and free space. Then i could start over (WITHOUT KDE THIS TIME)

Is there a way to do this??

Please help

When you format the partitions, it will wipe them clean.

---

### Post by lenswipe on 2007-12-15
> **EDavidBurg said:**
> When you format the partitions, it will wipe them clean.

i know but i just dont know what to click on what to go to etc....

---

### Post by jken146 on 2007-12-15
You can use gparted in the Ubuntu live CD to format partitions.  I believe Vista also has a partitioning tool.

---

### Post by lenswipe on 2007-12-15
> **jken146 said:**
> You can use gparted in the Ubuntu live CD to format partitions.  I believe Vista also has a partitioning tool.

thanks where is gpart?

[EDIT] Found gpartedit

next question; How do i format a partition in here? i want to wipe it completely so its toaly empty with NOTHING on it

---

### Post by sirdilznik on 2007-12-15
If you have the check box checked (exactly like you do in the screenshot) then it will format the partition (wipe it clean like you want it) when you accept the changes.  Simply set the mount point of /dev/sda3 to / and keep everything else exactly like it is in that screenshot then accept changes.  that will do the trick.

Edit: you don't need Gparted, the installation will format the partition for you if you follow my advice.

---

### Post by lenswipe on 2007-12-15
> **sirdilznik said:**
> If you have the check box checked (exactly like you do in the screenshot) then it will format the partition (wipe it clean like you want it) when you accept the changes.  Simply set the mount point of /dev/sda3 to / and keep everything else exactly like it is in that screenshot then accept changes.  that will do the trick.

i did


look at the error box...

anyhoo it just seems to have sorted itself out for now...

i uninstalled KDE again and rebooted the laptop...

---

### Post by sirdilznik on 2007-12-15
The error box is because you didn't change the mount point (the mount point is /media/sda3 in the screenshot, it needed to be / )  Anyway if it all works now than that's good.

---

