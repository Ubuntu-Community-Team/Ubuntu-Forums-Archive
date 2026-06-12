---
title: "Unable to boot Ubuntu 10.10 Desktop (32 bit) in dual boot with Win 7 64 bit"
date: 2011-01-07
forum: Desktop Environments
---

### Post by crgal on 2011-01-07
I have a Sony VPCZ13C5E with Intel Core i7 M640 @ 2.8GHz and Windows 7 Prof 64 bit.
It has 4 x 122GB SSD's in one Volume type Raid 0 using Intel Rapid Storage Technology.

The installation prog did not offer to install alongside an existing (Win 7) system, however after installation I was able still to boot Win 7 from the Grub Menu, but the 
Linux option just gives the black screen of death.

Booting from the 10.10 LiveCD and running sudo fdisk - l gives "unable to seek on /dev/sda".
Also I have had a message "unknown filesystem type 'isw_raid_member' although I have forgotten where that came from!

The LiveCD shows that the filesystem does seem to have installed OK on the ext4 partion of 100Gb which I had 
kept for it, however it will not boot.

The results of Boot_info_script are shown in the attachment Results.txt

I have tried 
sudo mount /dev/mapper/isw_dijbjabefg_Volume07 /mnt 
and it gives no errors.

I then tried 
sudo grub-install --root-directory=/mnt/ /dev/sda 
which gave no errors but when I reboot and
choose Linux the result is still the black screen of death.

I understand that the problem may be one of Ubuntu drivers having to catch up with the latest technology but given that Ubuntu can partition the swap file and the ext4 system I seem to be so close.

Is there anyone out there who can give me some ideas? Please bear in mind that whilst I am a user with quite a few years of Ubuntu experience I am still a Newbie when it comes to the mechanics of Grub and digging under the bonnet.

---

### Post by ajgreeny on 2011-01-07
I think the problem is the raid setup you have, which the live CD can not handle properly, and shows in the results.txt as "unknown filesystem" on the devices.

I think you need the alternative-install CD for raid.

---

### Post by crgal on 2011-01-08
Thanks for your advice. I installed using the alternative 32 bit iso but got more or less the same result. I then had another try altering the raid parameters but that lead to nothing booting at all (not even windows) so I had to resort to a drive image restore! I obviously need help on the copious raid options.

---

### Post by crgal on 2011-09-10
I have solved this problem with help from

[http://www.adhocism.net/2011/05/installing-ubuntu-11-04-on-sony-vaio-vpc-z13m9eb/](http://www.adhocism.net/2011/05/installing-ubuntu-11-04-on-sony-vaio-vpc-z13m9eb/)

Search on VPCZ13C5E and see more details in my other thread.

---

