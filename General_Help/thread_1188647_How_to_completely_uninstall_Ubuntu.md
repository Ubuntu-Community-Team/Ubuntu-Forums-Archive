---
title: "How to completely uninstall Ubuntu?"
date: 2009-06-15
forum: General Help
---

### Post by Blackcamaro8 on 2009-06-15
Okay, i know what you're thinkin.
 "why would you want to uninstall something so cool!?"
and it's so i can start from a clean install.

i love ubuntu, but i recently made a clean install on a 10 GB HDD, and then i customized it the way i want, but now i want to transfer that to the old one's spot. 

the setup on the other one is quite messed up lol...

It's dual booted with windows. Windows is on a 20GB hard drive with a 500GB slave, and ubuntu is installed onto the slave... so i have no idea how to uninstall Ubuntu along with GRUB, and everything else it's installed. 

any help would be MUCH appreciated. thanks.

---

### Post by nothingspecial on 2009-06-16
First of all have a look [[COLOR="Red"]here[/COLOR]]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

You need to use the partition editor from a live cd to reformat your messed up ubuntu partition. Then install your custom ubuntu to your new partition.

Read up about it first and make sure you know what your doing before you do it. If you get it wrong you may end up destroying your windows installation. Any problems just ask.

---

### Post by kpkeerthi on 2009-06-16
1. Use **gparted live cd** and delete the partitions used for Ubuntu
2. Use **windows repair disk **and using **fixmbr** to get rid of Ubuntu.

Google on the highlighted texts to find out more.

---

### Post by talkingwires on 2009-06-16
Okay, you've got the installation you want on the HDD you're sharing with Windows, and want to move it over to your 10Gb HDD, then configure GRUB to work with the new setup? I'm just going off the top of my head here...

Wipe the small HDD, reformat it with your Linux file system of choice, and just copy everything over from your good installation. You shouldn't need to worry about boot-loaders and stuff like that, since Ubuntu'll be installed on your 10Gb drive which isn't setup as the boot device. You can use [Grub for Windows]("http://www.geocities.com/lode_leroy/grubinstall/") to modify Windows' bootloader to boot from the drive. Once you have things up and running, you can use Ubuntu to delete your old Linux partition and give the space back to Windows.

Of course, this'll only work if you installed a recent version of Ubuntu to begin with, one that doesn't insist on a /boot, /home/, /tmp, and root file system. I really don't know when Linux (or, just Ubuntu?) OS's made the switch over to a single partition.... I'm currently in the middle of my first Linux installation in at least five years after somebody knocked my laptop off a chair and killed the HDD.... heck, I'll just ask it here, does anybody know if this causes any stability or performance issues....?

---

### Post by jespdj on 2009-06-16
> **Blackcamaro8 said:**
> Okay, i know what you're thinkin.
 "why would you want to uninstall something so cool!?"
No, what I actually thought was "Oh, come on, this has been asked a thousand times before...". Please do a search, because this has also already been answered a thousand times before.

---

### Post by StGeorge on 2009-06-16
Yeah but do not Search the Ubuntu Site it is dreadful for finding answers unless you live in it and know the right question.

Use Google if you wish to ask a question relating to Ubuntu just put ubuntu into the search first.

Besides who wants to answer a silly question after they do a Search.

Ridiculous behaviour by Websites if you ask me.

Oh and get yourself a copy of this first:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

It has saved me loads of times after grub has completely f....d up my computer.

Along with FireFox3, (the worlds slowest browser), Grub has to be the worlds worst boot loader.

Oh and if you have a question then ask it in the Forum, that it is what it is for.

If you search around after asking the question, you might find you get a competent reply, while searching can be a real pain.
Besides. The more a question is asked, the more likely the answer will appear in Search Engines. ASK AWAY.

---

### Post by Blackcamaro8 on 2009-06-17
Okay you guys, none of what any of you have said has really helped me all that much.

but i love that last guy's response to the whole search thing... Lol



Allow me to re-explain myself in a better way.

The 20GB is the master, the 500 is the slave.

The 20GB has an installation of WinXP on it, and the entire drive is dedicated to that.
The 500GB is split in half, one part NTFS file system, the other half is the ubuntu file system (can't currently remember the name.).  The ubuntu file system is where ubuntu is located, and even though i've restored the boot sector on (C:) which is the 20, it still shows up as GRUB.

I have a copy of Windows 7 Release Candidate that can just format a partition and then run off of it.  Would it be safe to just eliminate Ubuntu altogether without any changes, or would it screw up booting?


I believe this is happening at startup:


Bootsequence scans C: and D:
Bootsequence chooses D: (grub)
GRUB shows up.

i THINK it's skipping the C: bootsector.

but would it be safe to just eliminate ubuntu?


i still have it on that extra(non-attached) 10GB and i'll use it occasionally.

---

### Post by rohitfeb14 on 2009-06-17
Delete the ubuntu drive and format it using ntfs or fat32... whatever u want..
then Fix the MBR using the windows installation disc..

On VISTA:  Go to dos prompt of repair and type BootRec.exe\FixMbr
On XP: at dos, type fixmbr
:p

[SIZE=7]By the way why are u doing so.... removing ubuntu!!!!![/SIZE]

---

### Post by StGeorge on 2009-06-17
You really do want to download system restore and burn it prior to doing what you wish to do.

But for what it's worth the main thing is to edit your menu.1st so that your XP is first boot.

I think its gedit /boot/grub/menu.lst

I'm in CoLinux so don't have booting issues.

You want to put the XP entry at the top of the boot list

I always copy the Windows entry so that on boot up you will see 2 entries for your XP.

Reboot your computer to ensure you are booting Windows first.

Then if you use the System Restore disk you will find a Gparted app in there.

You can then Format the Linux Partition with it. You can move Partitions with it.

You can also use the System Restore to Rewrite you Windows MBR if you wish.

It also has Test Disk in it a Powerful Tool to Regain Lost Partitions.

It will also find Windows or Linux Partitions.

Get it you will not be disappointed. It has saved me on numerous occasions. (always whenever I was getting rid of Ubuntu, that grub is a real pain in the rear).

You should also if you are Re-installing Linux on the 500 HD put the Linux OS at the beginning of the HD and put other Windows OS's after it. So move your Windows OS up the drive leaving the free space for Linux at the beginning.

Personally I would get yourself Portable Ubuntu and run it within your main OS. You can make a dedicated drive for it dump it on that and you are off and running.

[http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/)

Good Luck

oh and to answer your question. NO it is not safe just to overwrite Ubuntu.

For others considering it you really should be looking at all the comments in this Post first.

---

### Post by Blackcamaro8 on 2009-06-17
Yo guys, nevermind. 

I ended up screwing up and fixing the bootsector of the wrong drive, which, somehow in turn, corrupted my 500GB hard drive....

so i had to re-install everything.

thanks for trying to help anyway. 
:(:(:(:(:(:(:(:(

---

