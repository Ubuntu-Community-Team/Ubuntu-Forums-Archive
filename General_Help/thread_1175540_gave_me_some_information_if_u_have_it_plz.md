---
title: "gave me some information if u have it plz"
date: 2009-06-01
forum: General Help
---

### Post by gawadelnil2002 on 2009-06-01
For real i was using ubuntu about year ago and i still using it now as my primary and the only operating system on computer futji siemens and it works great with it and i met alot of bugs in my first time logging on ubuntu but now with juanty i feel very comfortable cause i cured most all of mu bugs
Note : that is the first time i use ubuntu forums

my question is about some informations i want to know 
  i tried ti install debian and i installed it 2 weeks ago on another computer to see it is really better than ubunt as people says or its just basic operating system but i found it as very basic operating system and u need to do alot of thing very alot to reach the efficiency of ubuntu working on it
any way the most things that made me crazy that io couldnt mount my partitions there like ubuntu 8.04 tell 9.04 do, there i need to go to fstab and write my mount point and how it will work if its auto for all usrs and stuff u know, but in ubuntu i just click the partition name form my places menu and it opens after asking about my usr password not even the root password just the usr password and it opens and i can write and change everything in the partitions 
so what is the difference why is that and that?
is ubuntu have additional software that it dosnt exist in debian or what and if it have what is that software ?
that was the informations i wanna know do u have it ? :popcorn:

---

### Post by mb_webguy on 2009-06-01
Most software available in the Ubuntu repositories is available in the Debian repositories as well.  Just because it's available, however, doesn't mean it's installed by default, or configured the same.  Once thing you can do to try to get Debian to work more like Ubuntu is to make sure the same packages are installed on the Debian system.

The first thing you need to do is get a list of the installed packages on the Ubuntu system.  On your Ubuntu machine, open the terminal and enter the following command:```
dpkg --get-selections | grep -v deinstall > ~/ubuntu-packages
```This will create a file called "ubuntu-packages" in your home directory which contains a list of all of the packages currently installed on Ubuntu.  Move this file to your Debian system by whatever means you want -- USB drive, over the network, emailing it to yourself, etc.

Now to install those packages in Debian, use the following commands.```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg --set-selections < ubuntu-packages
sudo dselect
```This will open a dselect session.  Type "/" to install all of the marked packges.  Once it's done, type "Q" to exit.

Some of the packages, particularly the Ubuntu-specific ones like ubuntu-desktop, will fail to install, since those packages don't exist in the Debian repositories.  These, however, tend to be metapackages that simply allow you to install a number of other packages which *will* be installed.  If you're using PPAs or other third-party repositories, you'll of course need to add them to your Debian software sources in order to install the associated packages.  Packages installed from PPAs or third-party repositories intended for Ubuntu *should* work just fine on a non-Ubuntu Debian-based system, but there aren't any guarantees.

Again, just because the same packages are installed, it doesn't necessarily mean the software will be configured the same.  One way to try to remedy this is to backup all of the configuration files in your Debian home directory, then copy the configuration files in your Ubuntu home directory to your Debian machine.  You will probably want to do this selectively, since it's possible that some of the configuration files point to files or locations that don't exist on the Debian system, and therefore will cause some problems.  Once you've done this with your user configuration files, you can do the same with the system configuration files found in the /etc directory.

---

### Post by gawadelnil2002 on 2009-06-01
for real im very greatful that u answered me (mb_webguy) very fast like this and posted all of this infor mation for me ,and its very valuble and i did made list of application installed on my ubuntu now and i was very happy that i can do that but i still want to know what package that cause the difference beween ubuntu and debian in the subject of mounting partitions and how to configure it .........thank u very much

---

### Post by gawadelnil2002 on 2009-06-01
One thing else i forget to mention,debian is faster than ubuntu and if i installed all package installed in ubuntu on debian i think it will behave like it and become slow, ofcourse i know u didnt say that i have to install all , but i say that to reasonize why i need to know only the difference in mounting partition subject and thank u again very very very much

---

### Post by ActiveFrost on 2009-06-01
*ntfs-3g* should do the job ( mount NTFS partitions ).

---

### Post by gawadelnil2002 on 2009-06-01
> **ActiveFrost said:**
> *ntfs-3g* should do the job ( mount NTFS partitions ).

look dear ntfs-3g really makes u can read the ntfs partitions and can mount it but it dosnt make the mounting itself behave like ubuntu , i mean in ubuntu u just see the partitions in places menu and click it and its open after taking ur password that is all ,in debian u have to go to the terminal do that manually or to edit fstab , and in ubuntu the fstab dosnt have in entry for logical partions just it have the entries of the filesystem and swap partion , and incase of debian u have to add logical partitions entry there (fstab) to let u mount it at start up or do what u want to do with it ,offffffffff,i talk so much :D

---

### Post by ActiveFrost on 2009-06-01
> **gawadelnil2002 said:**
> look dear ntfs-3g really makes u can read the ntfs partitions and can mount it but it dosnt make the mounting itself behave like ubuntu , i mean in ubuntu u just see the partitions in places menu and click it and its open after taking ur password that is all ,in debian u have to go to the terminal do that manually or to edit fstab , and in ubuntu the fstab dosnt have in entry for logical partions just it have the entries of the filesystem and swap partion , and incase of debian u have to add logical partitions entry there (fstab) to let u mount it at start up or do what u want to do with it ,offffffffff,i talk so much :D

By the first, I'm not your wife ( "dear" means the same as darling and .. yeah, it's used to refer to a wife/girlfriend ) :D
On-topic : if you are looking for an automated partition mounting ( like you said, partitions are automatically visible in your menu ), gnome-volume-manager might help you ( [http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html](http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html) ).

---

### Post by Chronon on 2009-06-01
It sounds like you simply don't like the way the file browser is configured.  Is that right?  I never had to edit the fstab to access any partitions when I used Debian Edgy.

---

### Post by gawadelnil2002 on 2009-06-01
> **ActiveFrost said:**
> By the first, I'm not your wife ( "dear" means the same as darling and .. yeah, it's used to refer to a wife/girlfriend ) :D
On-topic : if you are looking for an automated partition mounting ( like you said, partitions are automatically visible in your menu ), gnome-volume-manager might help you ( [http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html](http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html) ).

ofcourse u r not my wife or my girl friend hahahahahhahahaha :D, its culture differences , here egyptions always they use this friendly words to talk to other people , and this words have nothing behind it except friendly talk , im going now to open the link in ur post and see what u got and thank u for ur post very much

---

### Post by evermooingcow on 2009-06-01
I think what you're looking for is udev and maybe autofs. In general if you want all GUI I think you should stick to Ubuntu.

---

### Post by gawadelnil2002 on 2009-06-01
> **ActiveFrost said:**
> By the first, I'm not your wife ( "dear" means the same as darling and .. yeah, it's used to refer to a wife/girlfriend ) :D
On-topic : if you are looking for an automated partition mounting ( like you said, partitions are automatically visible in your menu ), gnome-volume-manager might help you ( [http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html](http://www.linuxforums.org/forum/debian-linux-help/140363-solved-solved-lenny-automount-ntfs-partition-usb-other-removable-media.html) ).
i opened the link and i see that he use gnome-volume-manager to auto mount the partitions but in ubuntu 9.04 ubuntu 8.04 ubuntu 8.10 dont have gonme-volume-manager installed on it by default and we all know that we can access partions in very easy way in ubuntu easier than debian like i discribed in my first post, so we dont know what is the difference till now and im searcging some webpages now maybe i will see something help me to know and apply that thier in debian ;)

---

### Post by gawadelnil2002 on 2009-06-01
> **evermooingcow said:**
> I think what you're looking for is udev and maybe autofs. In general if you want all GUI I think you should stick to Ubuntu.
i think u r right but we have to stuck with ubuntu as u said , we have to know how ubuntu works and how it manages things if u want to be stuck with it :) to give urself the appility to cure and repair what get damaged in ur operating system , it seems that i want to be programmer but for real i think its our rights to know how is everything going on and how to mamange it , not just take the live cd and install and search for the solutions for the bugs u find and no more , i think most of our problems comes from that we dont know alot about how linux operating systems work...................... i said alot of i think today and i think i dont have to say it again :D

---

