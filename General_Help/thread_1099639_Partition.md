---
title: "Partition"
date: 2009-03-18
forum: General Help
---

### Post by pedrom169 on 2009-03-18
i have a 3 hard drives

a 80gb holding ubuntu
a 40gb holding windows xp
and a 160gb doing nothing.

I want to make 140gb of the hard drive as my home drive for ubuntu
and 20gb as a way of swapping files over from ubuntu to xp and vice versa.

Could someone help me doing this?

---

### Post by taurus on 2009-03-18
You need to partition the 160GB harddrive into two:  140GB for /home and 20GB for sharing.  

Here's a guide about creating a separate /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by pedrom169 on 2009-03-18
what format should i put my 20gb one so both ubuntu and windows can see?

Thanks

---

### Post by pedrom169 on 2009-03-18
double post. Damn n95 lol.

---

### Post by taurus on 2009-03-18
Either fat32/vfat or ntfs although you cannot store a file larger than 4GB with fat32/vfat.

---

### Post by pedrom169 on 2009-03-18
thank you. I doubt i would have anything bigger than 4gb. 

What would be the best way to format the hard drive. It is currently as ntfs and partition it?

Thanks

---

### Post by taurus on 2009-03-18
You can use gparted from Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by MaindotC on 2009-03-18
You can make the partition ext3 but you need to install a program in your windoze partition called [FS Driver](http://www.fs-driver.org/).  It says ext2 but ext3 works as well.  This way you don't run into any size issues stated by taurus - which I didn't know until now.

---

