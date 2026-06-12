---
title: "Disk Partition during Install"
date: 2005-12-03
forum: Desktop Environments
---

### Post by anti-infective on 2005-12-03
I’m installing Ubuntu5.10 in my PC. It has a 120GB HDD divided into two with Windoze Xp installed in the first partition and nothing on the second. In the partition menu of Ubuntu (during installation), it can only see one 120GB partition and not two 60GB partitions. I’m afraid that if I ask Ubuntu to partition the 120GB that it might erase all its contents Widoze OS and files included. What should I do?

Pls note that partition 1 is FAT32 and Partition 2 is NTFS formatted (by windows).

---

### Post by Koybe on 2005-12-03
It's strange... anyway, try going back to your windows, erase the NTFS partiton you're planning to use for ubuntu. Reboot on ubuntu cd and try installing in the free space.

---

### Post by aysiu on 2005-12-03
During installation, do you ever get to a screen like this one? If so, select "Manually Edit the Partition Table."

---

### Post by amohanty on 2005-12-03
Just wondering how you were able to get the screenshot?

Thanks.
AM

---

### Post by anti-infective on 2005-12-03
[QUOTE=Koybe]It's strange... anyway, try going back to your windows, erase de NTFS partiton you're planning to use for ubuntu. Reboot on ubuntu cd and try installing in the free space.[/QUOTE]

Sorryfor the ignorance but how do i do that? when i right click the drive icon the only option i have is "format". shall i load up my windows xp installer disk and erase from there?

---

### Post by aysiu on 2005-12-03
[QUOTE=amohanty]Just wondering how you were able to get the screenshot?[/QUOTE] I actually stole it from [this amazing tutorial](http://users.bigpond.net.au/hermanzone/).

---

### Post by anti-infective on 2005-12-03
[QUOTE=aysiu]During installation, do you ever get to a screen like this one? If so, select "Manually Edit the Partition Table."[/QUOTE]

yes i do get this window. but  it sees only one "HDD/Partition". and when i click the 120GB partition it says that it will "erase" the drive to create a partition

---

### Post by Koybe on 2005-12-03
[QUOTE=anti-infective]Sorryfor the ignorance but how do i do that? when i right click the drive icon the only option i have is "format". shall i load up my windows xp installer disk and erase from there?[/QUOTE]

I think if you manually edit as aysiu told you, you should see both partition and select one for deletion. Linux is not using NTFS or FAT32 partition for his system, it uses another type of filesystem : ext3 commonly.

So if you can't see anything during installation go to your windows system, right-click "My computer" icon and then "Manage". Go to the disk partitionner and free the space you want for ubuntu. Then having free space on your disk, the installation will be easier.

---

### Post by aysiu on 2005-12-03
[QUOTE=anti-infective]yes i do get this window. but  it sees only one "HDD/Partition". and when i click the 120GB partition it says that it will "erase" the drive to create a partition[/QUOTE] So after you select "Manually edit the partition table," you get something like this? (Well, with 120 GB NTFS instead of 30 GB FAT32, of course.)

I'm just trying to confirm that I understand exactly what the problem is.

---

### Post by anti-infective on 2005-12-03
[QUOTE=aysiu]So after you select "Manually edit the partition table," you get something like this? (Well, with 120 GB NTFS instead of 30 GB FAT32, of course.)

I'm just trying to confirm that I understand exactly what the problem is.[/QUOTE]

something like that but with no smily face

IDE1 master (nda) - 120.0GB ST3120022A
pri/log 120GB freespace

when i click the pri/log it says it will create a partition on this drive and asks me how big the partition i want it to be. but im afraid that it will erase all 120GB including my files

---

### Post by aysiu on 2005-12-03
[QUOTE=anti-infective]something like that but with no smily face

IDE1 master (nda) - 120.0GB ST3120022A
pri/log 120GB freespace

when i click the pri/log it says it will create a partition on this drive and asks me how big the partition i want it to be. but im afraid that it will erase all 120GB including my files[/QUOTE] Hm. It's not seeing your partitions, then, for some strange reason. A live CD may help. I'd advise Knoppix, but you can use a Ubuntu live CD as well.

With the live CD, you can format your unused partition with QTParted (Knoppix) or GParted (Ubuntu).

---

### Post by Brent Dax on 2005-12-03
[QUOTE=anti-infective]I’m installing Ubuntu5.10 in my PC. It has a 120GB HDD divided into two with Windoze Xp installed in the first partition and nothing on the second.[/QUOTE]
Is this XP Home or XP Pro?  If it's the latter, I seem to remember that there's some kind of special partition format it can use, which Linux might not be able to handle.

---

### Post by amohanty on 2005-12-03
You can also use a Win98SE boot disk from bootdisk.de and use fdisk to do what aysiu suggested.

AM

---

### Post by anti-infective on 2005-12-03
Got it to work guys. Thanks. I didnt notice that i just "erased" and not "deleted" the second partition:p 

now how do i connect to the internet using a dial-up account? i cant seem to find the usual window in XP and mac where you have to input the username, password and dial up number

---

### Post by amohanty on 2005-12-03
System->Administration->Networking-> Select modem click on configure

Then at the terminal:
pon
poff

This is all assuming your modem has been recognized by Ubuntu.

HTH
AM

---

### Post by anti-infective on 2005-12-04
[QUOTE=amohanty]System->Administration->Networking-> Select modem click on configure

Then at the terminal:
pon
poff

This is all assuming your modem has been recognized by Ubuntu.

HTH
AM[/QUOTE]

configured the modem. what modem port do i use? when i tried to auto detect it  says "could not autodetect modem device - check that the device is nor buzy and that is attached correctly attached to the computer".

when i looked at device manager it says : Vendor- Conexant, Device-HSF 56k HSFi Modem. but in reality im using a D-Link 562IS modem

---

### Post by amohanty on 2005-12-04
> Vendor- Conexant, Device-HSF 56k HSFi Modem. but in reality im using a D-Link 562IS modem

Most modems use a modem chipset. It could be that the modem you have uses the Conexant chipset.

When you say you use a D-Link modem, is the DSL/cable modem you are talking about or the PCI modem card/built in modem vendor?

AM

---

### Post by anti-infective on 2005-12-04
[QUOTE=amohanty]Most modems use a modem chipset. It could be that the modem you have uses the Conexant chipset.

When you say you use a D-Link modem, is the DSL/cable modem you are talking about or the PCI modem card/built in modem vendor?

AM[/QUOTE]

it is actually a dial-up/telephone modem. internal and PCI i think

---

### Post by Koybe on 2005-12-04
[QUOTE=anti-infective]pri/log 120GB freespace[/QUOTE]
I don't know why... but it's like you got nothing on your hard drive :confused:

---

### Post by Zeroedout on 2005-12-04
[quote=anti-infective]it is actually a dial-up/telephone modem. internal and PCI i think[/quote]
 
 Yup, what you got their is a winmodem, welcome to hell. Now you gotta pay this fatass SOB some cash for a linux driver. Here is their website, [http://www.linuxant.com/](http://www.linuxant.com/) . These drivers are not free software, and i belive they released some crippled version of the driver for free, however, I am not sure if they do anymore. I could never justify paying them, so when I had dialup, I just used windows; I jumped on the broadband train as soon as it came. If linux and the internet are really important to you, then I guess you'll have to dish out the cash. You may also be able to get the crippled version running, but man, i remember using that thing, and it was shit. I think it capped your connection speed and all sorts of other bullshit. Anywho, good luck, hope you find a solution.
 
 Note: If you feel like burning down their corprate HQ, I already looked in the contacts page, they're smart nuff not to leave a phone number or snail (anthrax) mail address.

---

### Post by rsgooch on 2005-12-04
[QUOTE=anti-infective]it is actually a dial-up/telephone modem. internal and PCI i think[/QUOTE]

It sounds like you have a win modem.  This type of modem is considered a host based modem. What that means is windows provides the higher level functions of the modem.  This modem is basically hardware without smarts. The easy way to solve this problem is to connect and external modem to your serial ports or use a non HSF, HSP (winmodem) device.  Or you can do it the hard way and check [http://linmodems.org/](http://linmodems.org/) for supprt for your modem under linux. Conexant has released a driver for linux that may work for you (YMMV).  

Later,
Rueben

---

