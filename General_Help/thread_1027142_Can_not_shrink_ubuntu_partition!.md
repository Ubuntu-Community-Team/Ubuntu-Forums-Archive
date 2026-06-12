---
title: "Can not shrink ubuntu partition!"
date: 2008-12-31
forum: General Help
---

### Post by evilminininja on 2008-12-31
I need to put more space on my windows partitionm so I decided to shrink my ubuntu partition. After booting up with the livecd, I try and shrink it to no success. I was told in the error details (is that what you call them?) that:
GParted 0.3.8

Libparted 1.8.9

Move /dev/sda3 to the right and shrink it from 71.62 GiB to 51.29 GiB  05:06:57    ( ERROR )
     	
calibrate /dev/sda3  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 162368955
end: 312576704
size: 150207750 (71.62 GiB)
calculate new size and position of /dev/sda3  00:00:00    ( SUCCESS )
     	
requested start: 205021530
requested end: 312576704
requested size: 107555175 (51.29 GiB)
new start: 205021530
new end: 312576704
new size: 107555175 (51.29 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  05:03:24    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

359239 inodes used (8.29%)
9583 non-contiguous inodes (2.7%)
# of inodes with ind/dind/tind blocks: 16258/287/0
3544097 blocks used (20.47%)
0 bad blocks
1 large file

317506 regular files
21145 directories
69 character device files
26 block device files
4 fifos
115 links
20443 symbolic links (19504 fast symbolic links)
37 sockets
--------
359345 files
e2fsck 1.41.3 (12-Oct-2008)
shrink filesystem  00:00:02    ( ERROR )
     	
resize2fs /dev/sda3 53777587K
     	
resize2fs 1.41.3 (12-Oct-2008)
Please run 'e2fsck -f /dev/sda3' first.

check filesystem on /dev/sda3 for errors and (if possible) fix them  00:03:16    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

359239 inodes used (8.29%)
9583 non-contiguous inodes (2.7%)
# of inodes with ind/dind/tind blocks: 16258/287/0
3544097 blocks used (20.47%)
0 bad blocks
1 large file

317506 regular files
21145 directories
69 character device files
26 block device files
4 fifos
115 links
20443 symbolic links (19504 fast symbolic links)
37 sockets
--------
359345 files
e2fsck 1.41.3 (12-Oct-2008)
grow filesystem to fill the partition  00:00:15    ( SUCCESS )
     	
resize2fs /dev/sda3
     	
Resizing the filesystem on /dev/sda3 to 18775968 (4k) blocks.
The filesystem on /dev/sda3 is now 18775968 blocks long.

resize2fs 1.41.3 (12-Oct-2008)

========================================

In windows when i try and shrink ubuntu I get an error message. What is wrong? The non-contiguous space? How do i fix that? I have tried this over and over again.

---

### Post by xenolalia on 2009-01-01
I have noticed that for whatever reason, the GParted live CD tends to work better than GParted running in ubuntu.  I think this is because the GParted live CD is all-around much simpler than ubuntu -- fewer elements, fewer factors, fewer things to check, fewer things that can go wrong :D.  You can download the iso here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).

Good Luck!
Xenolalia

---

### Post by bumanie on 2009-01-01
> **xenolalia said:**
> I have noticed that for whatever reason, the GParted live CD tends to work better than GParted running in ubuntu.  I think this is because the GParted live CD is all-around much simpler than ubuntu -- fewer elements, fewer factors, fewer things to check, fewer things that can go wrong :D.  You can download the iso here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).

Good Luck!
Xenolalia

I agree, but I think the main reason the gparted live cd is better is because it is a dedicated tool, rather than being an add-on to an OS.

---

