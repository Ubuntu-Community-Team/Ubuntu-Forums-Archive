---
title: "Installing SUSE on free partition"
date: 2009-04-17
forum: General Help
---

### Post by Firestom on 2009-04-17
Hey!

I installed my Ubuntu intrepid partition on my hard drive a while ago. I remember making 4 partitions or so: One for Ubuntu, One Free to eventually install Windows (but my mind changed), One for the home directory and One for Swap. However, I would like to use my partition to install OpenSUSE (Which I like for it's powerful Yast interface notably).

How can I know which partition is left to install an OS (in this case SUSE), and how can I install SUSE on this partition?

---

### Post by zvacet on 2009-04-18
In synaptic install **gparted** and you will find it under system>admin.With it you will see all your partitions and I believe you will see unused one.Suse should also be capable of recognizing unused partition.Install Suse on that partition.

---

### Post by Jammy4041 on 2009-04-18
> I installed my Ubuntu intrepid partition on my hard drive a while ago. I remember making 4 partitions or so: One for Ubuntu, One Free to eventually install Windows (but my mind changed), One for the home directory and One for Swap. However, I would like to use my partition to install OpenSUSE (Which I like for it's powerful Yast interface notably).

How can I know which partition is left to install an OS (in this case SUSE), and how can I install SUSE on this partition?

You can only have 4 physical/extended partitions. You can have as many logical partitions inside those extended partitions as you like, though.

Windows cannot boot by default on a logical partition; instead it has to be installed on a physical partition.

I have gParted installed on my hard drive inside its own partition; I followed the instructions at [http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)

I suggest that you follow the instructions on the link above; or you can use an ubuntu/SUSE Live CD. The  gParted Editor from the Ubuntu repos will not enable you to edit the hard drive, and you have a higher risk of data loss. 

Remember, a painter cannot paint on the same spot he is standing on; and the same is true for a partition editor.

I have a something-boot of Windows 7, Windows XP, Ubuntu, Fedora and my various tools, accesible from a dedicated GRUB menu. I found the link at [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition) very useful.

Then it is a case of setting up GRUB for a triple boot. I believe SUSE, unlike Fedora and other Linux distros, have a symlink to their most recent kernels, making updating easy, if you decide to go down the dedicated GRUB partition route. In any case you can easily create a symlink.

Having a dedicating partition for the GRUB loader also means that you can experiment with other Linuxes if you wish.

---

### Post by Firestom on 2009-04-18
In fact, I have three physical partitions: sda1 (Ubuntu), sda2 and one unallocated. Inside sda2, I have sda5 (Linux-Swap) and sda6 (/home). If SUSE can install itself on an unallocated partition, I will just run install SUSE using the install CD.

Thanks a lot!

---

### Post by Firestom on 2009-04-19
I have finally installed SUSE on my hard drive using Net install. However, now I can't access my Ubuntu partition. SUSE installed itself on a logical partition on /dev/sda2 and shared my /home and my swap partition, which is just perfect. Two problems occured: First, SUSE doesn't read files from my /home, like it has it's own. Second, to boot into Ubuntu, I have to through SUSE's GRUB, and then passes on to Ubuntu's GRUB. However, it can't boot Ubuntu. It prints ```
Error 15: File missing
```. I haven't memorized everything printed on the screen but if it can be useful I can go get it.

Is there a way to access Ubuntu using external media (I've heard of a method using a LiveCD, but I don't know much about it) and how can I fix the problem. Are there some specific things (like commands) I can do to get back on track?

Thanks for replying!

---

