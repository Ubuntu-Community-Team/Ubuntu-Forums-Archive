---
title: "The Media Direct Button"
date: 2008-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bluemotion on 2008-09-25
Hi all,
am sure, like most you guys, as soon as i unboxed my dell i decided to scrap my recovery partion. and it occured to me the button (dell media direct button) isnt doing anything, and thought that would be perfect to launch ubuntu.

i had a quick google and as it turns out its been done, and then i tried...

[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html)

i made the mistake of installing grub to a ntfs partition :(:(, but i managed to fix that and grub is installed as usual:).

i have been using ubuntu for about 2 years now, but im hardly a pro. and i dont hate vista, it works pretty well on my m1330 anyway.


i was if someone could tell walkme through it.:popcorn:

Edit i realized including my partition table would be useful

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       12876    52227315    5  Extended
/dev/sda3           12877       24321    91931962+   7  HPFS/NTFS
/dev/sda5            6375        7590     9767488+  83  Linux
/dev/sda6            7591       12453    39062016   83  Linux
/dev/sda7           12454       12876     3397716   82  Linux swap / Solaris


-sda1 - vista
-sda2 - extended
   --sda5 - ubuntu
   --sda6 - documents (mounted in vista using an ifs driver)
   --sda7 - swap
-sda3-storage drive (used for storage,accssed in vista and ubuntu, iinstall the occasional windows game on it, hence the NTFS)

the guides say i have to move grub a primary partition (im not sure what that is)

---

### Post by kry10 on 2008-09-26
Hi:

Interesting page you found (I'm going to try this myself :) )

Based on his instructions and your partition table, it looks like the partition you want to install grub on is sda2 - it's the "primary" partition your ubuntu install is on (i.e.: it contains the "extended" partions - sda5,6 and 7 - with your linux info). So, this would be your grub install:

grub-install /dev/sda2

Then, in Windows, with the Dell Media CD, you'd run this:

cd H:\DellKit
rmbr.exe DELL 1 2

Since "1" is your Windows partition, and "2" is your Ubuntu (or, more accurately, where you installed grub in the previous step).

Hope this helps!

---

### Post by Bluemotion on 2008-09-27
I could have Sworn i tried that, but evidently i didnt.
Thankyou ever so much! :) :) :)

---

