---
title: "GParted only resizes NTFS by 2 MB"
date: 2008-12-14
forum: General Help
---

### Post by happinesskills on 2008-12-14
I am getting rid of Vista (I hate it. I want to stab it in it's tiny little ballsack!) & have installed Ubuntu, got everything I wanted, backed up my stuff from Vista on to an external hard drive.

My problem is that the NTFS partition that Vista was on can't be Resized. In the old Ubuntu setup disc I had, it gave me an option to create a new partition that Ubuntu would go on to. That disc somehow got errors & I had to download another one. The new disc didn't do that & so I selected 'Guided - Use largest continuous free space'. Now I DISTINCTLY remember the old disc said I could reduce my Vista Partition to about 60GB. 

When I went in to Gparted, my Vista partition is about 140GB & my Ubuntu Partition is about 8GB (You can see in my screenshot). Now when I went to resize the Vista partition it only let me resize it by 2MB. why? can I fix this?

---

### Post by Partyboi2 on 2008-12-16
To increase the size of ubuntu you will need to either delete Vista, ntfs (sda2) and increase the size of ubuntu to use the newly unallocated space. Or if you still need to keep vista you can use the resize tool that comes with vista to shrink it down. Try defragging before shrinking vista. Then use the ubuntu live cd gparted (System>Admin>Partition Editor) to resize your ubuntu installation. 
Remember the partitions need to be unmounted to work on them.

---

