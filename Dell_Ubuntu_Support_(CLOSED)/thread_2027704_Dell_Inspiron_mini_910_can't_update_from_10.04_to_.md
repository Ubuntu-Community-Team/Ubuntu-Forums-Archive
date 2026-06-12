---
title: "Dell Inspiron mini 910 can't update from 10.04 to 12.04"
date: 2012-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ssojjoss on 2012-07-16
Hi all

I have a Dell Inspiron mini 910 that I haven't used in a while so decided to update the ubuntu 10.04 on it to ubuntu 12.04. I did this by opening the terminal and typing.
```
sudo do-release-upgrade -d
```
After a few minutes the terminal says that there is not enough free disk space. I should free at least an additional 912M of disk space on '/'. This is probably because the computer only comes with a 4GB hard disk however I did my best to remove as much junk as I could. I have used sudo apt-get clean and autoclean. I have got rid of residual config packages using synaptic package manager. I have emptied the trash and got rid of all files in the home directory.

I don't know what else I can get rid of in the file system. Any ideas?

---

### Post by OM55 on 2012-07-16
There is no direct way around getting the minimum space required for the upgrade.
During upgrade the size of hard drive required is MORE than during a fresh install. The reason being that often you have duplicate files (new and old) or merging files (old and new). Also the programs that do the upgrade need to be on the hard drive, again taking space.

4GB space is extremely small in technology technology (Western Digital stopped manufacturing the 640GB for laptops a while ago... so even those are hard to find...)

However, here are three possible solutions:
1. You can buy a compatible larger laptop hard drive, than use Image for Linux ([http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)) to create an image backup of your existing drive onto an external memory (USB Key, Compact Flash or USB drive).
Open your laptop and replace the old hard drive with the new one, then restore with Image for Linux the image backup onto the new drive. In the process allow it to expend the size of the partitions to the physical space available on the new hard disk.
Now you can go ahead and do your upgrade without problems.

2. Use GParted ([http://gparted.sourceforge.net]("http://gparted.sourceforge.net/")) to find any unused partitions that you can remove (for example, an old unused 'image restore' partition or alike). Many vendors like yours leave stuff like that on their laptops. Once you remove an unused partition, you can resize your main partition to take the extra space. This may give you enough space to upgrade.
However, keep in mind that when playing with the partitions you should feel that you know what you are doing. Otherwise, I suggest to avoid doing that or you might accidentally erase your entire drive!

3. May I suggest that instead of an upgrade you consider installing a fresh system?
For this the 4GB space would be sufficient and you would be able to select to install a very lean OS. Yes, you will need to set up your OS again, do some backups before and restorations after (documents, address books, emails etc) but if you are not comfortable with the first two options above, you are not left with too many options to get the latest Ubuntu on your laptop...

Keep in mind that sooner or later you would run into the space limit of the 4GB. It is really small in today's technology age. You can't even buy anymore a USB Key that small

---

### Post by ssojjoss on 2012-07-17
I had tried giving option 3 a try. It is an old laptop and there are no documents on it that I need (I have deleted them all now anyway) so I went for a fresh install of ubuntu 12.04 through a USB stick as the netbook doesn't come with a cd/dvd drive. However when I got to the installation screen with three headings telling you are connected to the internet, are plugged into the mains and showing if you have enough disk space (4.4GB), I obviously didn't have the 4.4GB disk space.

So I tried a few other OS. First mint needed something like 5.6GB. I tried xubuntu and lubuntu and they also needed the 4.4GB space to start.

I finally thought I would go really lightweight so I think I tried getting puppy linux on a USB but didn't manage it successfully.

Do you know any ubuntu like OS that I could do a fresh install with?

---

### Post by OM55 on 2012-07-17
Sorry, but I don't know of any other OS that would fit in that space... And if it would, you would be very limited in what you can add to it.

I think that replacing the hard drive with a bigger one would be the way to go...
A new internal laptop hard drive would be anywhere between $80-$130 while a new laptop would be as little as $250... you may consider simply buying a new laptop...

---

### Post by gerrman97 on 2012-10-22
go to the store (walmart, Kmart, Target etc.) and buy an 8 gig flash drive. find a computer with windows installed and download this item: Wubi.exe ( found on Ubuntu website)
plug the usb into the computer with windows
open up wubi.exe
then when it opens: on the drive selection, select your usb.
select the largest one that will fit on your flash drive
click the install button
when done plug:
plug it into your computer
turn it on
go into bios
boot sequence then select your usb
that should work. if not theres always windows xp
 
windows xp ran on a five gig hard drive for me

---

### Post by JRV on 2012-10-22
You need to install with the netboot CD to get around the 4 gig requirement.

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

---

