---
title: "e2fsck and Input/output error"
date: 2009-04-24
forum: General Help
---

### Post by usprey on 2009-04-24
Hi, I'm the happy owner of a 1TB WD external HDD, formatted to ext3. I started experiencing weird behaviour when trying to copy some specific files to my computer, resulting in an "Input/output error". In Intrepid i tried running e2fsck, always resulting in "e2fsck: aborted" without an exit code. Now it seems the, I assume, never libraries in Jaunty, can succesfully control and fix the hdd (GParted log included below).

So my questions are:
Is there anything seriously wrong with my external hdd?
Can I do anything to fix the Input/output error? 

```
GParted 0.4.3

Libparted 1.8.8
Kontrollér og reparer filsystemet (ext3) på /dev/sdb1  01:11:35    ( SUCCESS )
     	
kalibrér /dev/sdb1  00:00:00    ( SUCCESS )
     	
sti: /dev/sdb1
start: 63
slut: 1953520064
størrelse: 1953520002 (931.51 GiB)
kontrollér filsystemet på /dev/sdb1 for fejl og reparér dem hvis muligt  01:11:35    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sdb1
     	
Pass 1: Checking inodes, blocks, and sizes
Error reading block 72294925 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 17760263. Ignore error? yes

Force rewrite? yes

Error reading block 71729394 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729395 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729396 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729397 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729398 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729399 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729400 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729401 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71729648 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 71925802 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72286296 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72286310 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72286521 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72286536 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72482958 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72483184 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72646753 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72646978 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 72659895 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 18161677. Ignore error? yes

Force rewrite? yes

Error reading block 73007443 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 74940618 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 74940844 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 77800845 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 19120152. Ignore error? yes

Force rewrite? yes

Error reading block 77802895 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 19120152. Ignore error? yes

Force rewrite? yes

Inode 19120152, i_blocks is 718568, should be 702184. Fix? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences: -(77800846--77801869) -(77802896--77803919)
Fix? yes

Free blocks count wrong for group #2374 (0, counted=2048).
Fix? yes

Free blocks count wrong (84888632, counted=84890680).
Fix? yes


TLF29848831: ***** FILE SYSTEM WAS MODIFIED *****

15365 inodes used (0.03%)
1429 non-contiguous files (9.3%)
3 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 11464/7163/0
159299320 blocks used (65.24%)
0 bad blocks
2 large files

13222 regular files
2134 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
15356 files
e2fsck 1.41.4 (27-Jan-2009)
forstør filsystemet, så det udfylder partitionen  00:00:00    ( SUCCESS )
     	
resize2fs /dev/sdb1
     	
resize2fs 1.41.4 (27-Jan-2009)
The filesystem is already 244190000 blocks long. Nothing to do!

========================================
```

---

