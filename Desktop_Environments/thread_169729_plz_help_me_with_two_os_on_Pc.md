---
title: "plz help me with two os on Pc"
date: 2006-05-03
forum: Desktop Environments
---

### Post by armis on 2006-05-03
Hello,please if u can help me.I wan to use windows XP home edition,and ubuntu.Now curenly i have instaled only ubuntu on my computer,when i try to install windows xp,on the setup startup iget this eror.Windows setup canot find an hrd drives on your computer
Help how i can fix it.Ewerithing with hard drives is ok,they are concted,whats the problem???

---

### Post by manicka on 2006-05-03
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by mjm115 on 2006-05-03
You can also try [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by armis on 2006-05-03
you didint understand me,i have instaled ubuntu,i cant install windows because it sais that windows setup canot wind any hard disk drrivers

---

### Post by mbeach on 2006-05-03
The lesson I've learned about dual boot which includes Windows (and it's probably mentioned in the links provided) is that you want to install Windows first, then Linux.  Windows just doesn't want to play nice with other OS's already on the system whereas Linux will see that you have Windows installed, and can be installed on the partition of your choice.  I recommend installing Windows (which you say you can't - but if you were to create a Windows startup disk on another machine, then use that startup disk to format your hard drive you should be able to install Windows).  When you are finished installing Windows, using the Windows disk manager, create a suitable blank partition (right click on 'my computer' -> manage -> storage -> disk management) [or alternatively when you are first formatting your harddrive, only format a partition of the size you want for Windows].  Once Windows is happy, and you have a free partition, then install Linux into that free partition.

Maybe get a second opinion on this.  It's late and I'm tired.

Hopefully you didn't wipe out your Windows OS by mistake when you installed Linux.  The only reason I suggest using Windows to create that blank partition is that the Linux install process is not 100% clear to the first time installer when it comes to the disk partitioning section.

Good luck,
mb.

---

### Post by louis_nichols on 2006-05-04
[QUOTE=mbeach]The lesson I've learned about dual boot which includes Windows (and it's probably mentioned in the links provided) is that you want to install Windows first, then Linux.  Windows just doesn't want to play nice with other OS's already on the system whereas Linux will see that you have Windows installed, and can be installed on the partition of your choice.  I recommend installing Windows (which you say you can't - but if you were to create a Windows startup disk on another machine, then use that startup disk to format your hard drive you should be able to install Windows).  When you are finished installing Windows, using the Windows disk manager, create a suitable blank partition (right click on 'my computer' -> manage -> storage -> disk management) [or alternatively when you are first formatting your harddrive, only format a partition of the size you want for Windows].  Once Windows is happy, and you have a free partition, then install Linux into that free partition.

Maybe get a second opinion on this.  It's late and I'm tired.

Hopefully you didn't wipe out your Windows OS by mistake when you installed Linux.  The only reason I suggest using Windows to create that blank partition is that the Linux install process is not 100% clear to the first time installer when it comes to the disk partitioning section.

Good luck,
mb.[/QUOTE]

He doesn't need to go through all that trouble. he can just use the XP installer CD to wipe the HDD clean, then create partitions and format on of them as ntfs or fat32 to put win on it. Then put the Ubuntu installer in and let it do its thing with the other partitions. He just needs to save personal files stored under Ubuntu right now.

However, the problem being that the win install cd doesn't see a perfectly working hard drive... I dn't know why it might be. This is a question that might be better asked on a windows forum. Or, just ask microsoft directly. You bought a licence, you should get support for at least a while. E-mail them!

---

