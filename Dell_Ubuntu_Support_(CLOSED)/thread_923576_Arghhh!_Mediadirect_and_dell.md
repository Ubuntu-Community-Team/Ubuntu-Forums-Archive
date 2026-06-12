---
title: "Arghhh! Mediadirect and dell"
date: 2008-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JuBeZ on 2008-09-18
So I heard about this horrendous thing that happens when you press the dell mediadirect button. Shikes! So I thought hey, I'll prevent this from ever happening by deleting my Dell MediaDirect partition! YAY! Good idea right? I thought so too. When I reboot my laptop, (note I've NEVER pressed the Dell Mediadirect button at this point) I get the god damn grub error 17. So I go to youtube, where there is a fix posted for this problem. I give that a try, doesn't work. Luckily (or so I thought) I created a hard drive image with acronis true image. But just as I was about to restore it, I find out you get in major deep sh!t if you have Dell MediaDirect 2, but not 3. So most importantly, how do I know if I have MD2 or MD3? BTW, I'm running BIOS A09 if that helps any. 

Also, I threw in my Vista Recovery Disc and tried doing startup recovery and that hoo ha. Nothing happened. I entered fixmbr into the recovery console but it said it didn't recognize the command. WTF? I know it worked on XP for me before. Is there a different command for Vista? 

Until I hear from you much more knowlegeable people, I won't be restoring my Acronis just in case it makes my computer even more lovely. So right now, I'm somewhat computerless. 

BTW, it's a Dell XPS M1530 with a 200GB HDD, dual booting Vista and Ubuntu flawlessly until now. 

And one more thing, I LOVE DELL!

---

### Post by jespdj on 2008-09-18
I have an XPS M1530. When I got the laptop, I deleted everything except the very small system utilities partition (which is 100 MB or so) and installed Windows Vista and Ubuntu on it.

When I press the Media Direct button, no disasters happen - it just boots Ubuntu (my default OS), the only thing that happens is that it displays a Media Direct logo on the boot screen.

It might just be that you have a hardware error with your harddisk, which just by coincidence happened to appear for the first time when you pressed the Media Direct button.

---

### Post by JuBeZ on 2008-09-18
It happened after I deleted the media direct partition, so I don't really know what it is. I'm thinking I'll just restore from the HD image I made.I'm gonna make sure Dell Media Direct is removed this time when I restore. Does anyone know how to go about this? I need to restore the HD image because of all I have on it, but if I restore the MediaDirect partition will come along with it too... Hm....


BTW I have to do this tonight or tomorrow morning because I'll be on the road for college after that and I don't want to deal with this mess over there. So if anyone can help me before that, it would be greatly appreciated!:)

---

### Post by laurence91 on 2008-09-19
Where did you install grub too? The problem with media direct key is that it rewrites grub in the mbr when pressed and pretty much bricks the laptop. You need to install grub into your linux root partition preferably then remap the mediadirect key to boot your linux install.

I doubt you have media direct 2, dell didnt ship the m1530 with media direct 2 i dont think.

I have posted on this before but i cant remember the link to the page. ill have a look

Laurence

---

### Post by laurence91 on 2008-09-19
Here are the steps to remap the media direct key .......

Step 1. Install grub to a primary partition.Here im installing it to my last primary partition under which i have my linux extended partitions.(Even if you have it installed to MBR no problem..just install it again to another primary partition....the second step will overwrite your MBR)

grub-install /dev/sda4 

reboot to windows

Step 2. Put in the Media direct 3 CD that comes with your dell laptop.Start cmd (in vista u have to run as administrator)

cd H:\DellKit
rmbr.exe DELL 1 4

here 1 is for your Windows partition and 4 is for the partition which u have installed grub to )

Done.Shutdown.

Optional step. Set grub timeout to 0 in boot/grub/menu.lst and it wont show the grub menu.

Next time u press the power button it will boot into XP/Vista(Or XP + vista if u have both :-) ) and if u press Media Direct button it will boot into linux.


With thanks too

[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html)

where the information came from.

Laurence

---

### Post by anjilslaire on 2008-09-19
On Windows-based laptops with MediaDirect, the MD partion is hidden in and can't easily be deleted.
If you want it gone, zero the drive, as noted in [this thread]("http://ubuntuforums.org/showthread.php?t=745547"). 

Solved the problem on my 1420

---

### Post by bigbrovar on 2008-09-20
> **JuBeZ said:**
> So I heard about this horrendous thing that happens when you press the dell mediadirect button. Shikes! So I thought hey, I'll prevent this from ever happening by deleting my Dell MediaDirect partition! YAY! Good idea right? I thought so too. When I reboot my laptop, (note I've NEVER pressed the Dell Mediadirect button at this point) I get the god damn grub error 17. So I go to youtube, where there is a fix posted for this problem. I give that a try, doesn't work. Luckily (or so I thought) I created a hard drive image with acronis true image. But just as I was about to restore it, I find out you get in major deep sh!t if you have Dell MediaDirect 2, but not 3. So most importantly, how do I know if I have MD2 or MD3? BTW, I'm running BIOS A09 if that helps any. 

Also, I threw in my Vista Recovery Disc and tried doing startup recovery and that hoo ha. Nothing happened. I entered fixmbr into the recovery console but it said it didn't recognize the command. WTF? I know it worked on XP for me before. Is there a different command for Vista? 

Until I hear from you much more knowlegeable people, I won't be restoring my Acronis just in case it makes my computer even more lovely. So right now, I'm somewhat computerless. 

BTW, it's a Dell XPS M1530 with a 200GB HDD, dual booting Vista and Ubuntu flawlessly until now. 

And one more thing, I LOVE DELL!

happened to me once .. on my boss laptop .. we wanted me to install ubuntu for him .. so i deleted the media direct partition to get free space .. when i reboot grub gave an error .. i tried everything under the sun but it wont burge ..in the end i had to do a clean install of both vista and ubuntu ...

---

### Post by JuBeZ on 2008-10-02
Yeah... I clean installed Vista, restored my HD image, and eventually got my Ubuntu restored too, but it was real messy and had some errors, so I just clean installed Ubuntu.

---

### Post by Karpah on 2008-10-02
Hmm, I never had those sort of problems, I run the same setup as jespdj. Didn't touch the original Vista install, deleted the Dell MediaDirect and recovery partitions, installed Ubuntu on a separate partition, and now pressing the MediaDirect button just loads up the MediaDirect logo but the normal grub menu.

---

### Post by bendelebrown on 2009-05-19
I know this thread is old but I found it today when looking for info on rebuilding a box after a virus. I worried that the other partitions were infected and almost wiped them. I decided from past experience to investigate first and found a few interesting links to steps to make things work. So I will share one here in case it helps others who land on this old thread.

[(guide) How to boot ubuntu using MediaDirect Button - Notebook Forums and Laptop Discussion]("http://forum.notebookreview.com/showthread.php?t=182495")

---

### Post by disintergrator on 2011-01-31
[QUOTE=laurence91;5817764]Here are the steps to remap the media direct key .......

Step 1. Install grub to a primary partition.Here im installing it to my last primary partition under which i have my linux extended partitions.(Even if you have it installed to MBR no problem..just install it again to another primary partition....the second step will overwrite your MBR)

grub-install /dev/sda4 

reboot to windows

Step 2. Put in the Media direct 3 CD that comes with your dell laptop.Start cmd (in vista u have to run as administrator)

cd H:\DellKit
rmbr.exe DELL 1 4

here 1 is for your Windows partition and 4 is for the partition which u have installed grub to )

Done.Shutdown.

Optional step. Set grub timeout to 0 in boot/grub/menu.lst and it wont show the grub menu.

Next time u press the power button it will boot into XP/Vista(Or XP + vista if u have both :-) ) and if u press Media Direct button it will boot into linux.


With thanks too

[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html)

where the information came from.

Laurence[/QUOTE



I get stuck at the first step. When I try it, it says:
```
grub-install /dev/sda4 
Probing devices to guess BIOS drives. This may take a long time.
sed: can't read /boot/grub/device.map: No such file or directory
grep: /boot/grub/device.map: No such file or directory
/dev/sda4 does not have any corresponding BIOS drive.
```I have a Dell XPS M1330
Right now it seems to be flawlessly dual-booting XP & Ubuntu. 
Most, if not all drivers and updates are installed on both sides. 
It has a 160GB hd, and this is how it looks thru terminal using the df -h command:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              19G  3.3G   15G  19% /
none                  1.5G  324K  1.5G   1% /dev
none                  1.5G  204K  1.5G   1% /dev/shm
none                  1.5G   96K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda5              49G  269M   46G   1% /home
   
```My only concern now is the Media Direct button. I have tried many guides on remapping it, but always get an error message or something different than what the guide says should happen. Forgive me, for I am a newbie at Ubuntu, but I am learning a little bit. I have been coping with this annoyance and trying different guides since 2008 when I got the laptop. Any help at all would be greatly appreciated.

Also, in this [guide]("http://forum.notebookreview.com/dell-latitude-vostro-precision/231747-vostro-1500-boot-xp-form-mediadirect-button-ubuntu-power-button.html"), when I get to step 22, it says:
. Open the terminal (applications > accessories > terminal), and type...

 	Code:
 	sudo grub 
...followed by...

 	Code:
 	find /boot/grub/stage1 
...which will return... 

 	Code:
 	(hd0,2) 
But when I do it, I get into grub, but when I do the next command, this is what I get:
find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory






Dont know if that helps or not, but thought Id share.

---

