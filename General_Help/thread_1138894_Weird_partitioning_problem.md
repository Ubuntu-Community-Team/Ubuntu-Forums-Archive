---
title: "Weird partitioning problem"
date: 2009-04-26
forum: General Help
---

### Post by joelm2400 on 2009-04-26
Ok I have tried searching everywhere to figure this one out. Right now I have 4 HDDs and 6 main partitions (sda1, sda3, sdb1, sdc1, sdd1, sdd2 ) sda1 is the OS and extra space for some expansion. Sda 3 is for old windows games yet to be put on, sdb1 is music, sdc1 is video, sdd1 is space for pics, and sdd2 is space to be used just for downloads. Originally sda3 was to be used for picture and sdd1 was used for downloads, and sdd2 did not exist. I decided to reorganize partitions and create the new one. 

If I havent lost you yet, I'll get to my main problem. When I reorganized partitions i have some mystery used space that shows up even though the places they are mounted are completely empty. On Sdd1/2 the space on each partition is 22.78Mb each, not huge by any means but odd. The mystery space on sda3 sizes up to 561.58MB! The truly weird part is that when viewing partitions through Gparted where they were made, when viewing through discus shows a completely different size. Here is the output  from discus"

Mount           Total         Used         Avail      Prcnt      Graph
/                9.17 GB      2.53 GB      6.64 GB    27.6%   [***-------]
+ib/init/rw     501.1 MB         0 KB     501.1 MB     0.0%   [----------]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
/var/run        501.1 MB       304 KB     500.8 MB     0.1%   [----------]
/var/lock       501.1 MB         0 KB     501.1 MB     0.0%   [----------]
/dev            501.1 MB       168 KB     500.9 MB     0.0%   [----------]
/dev/shm        501.1 MB        76 KB     501.0 MB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+c/volatile     501.1 MB       2.3 MB     498.8 MB     0.5%   [----------]
+edia/music     74.47 GB     34.92 GB     39.55 GB    46.9%   [*****-----]
+edia/video    297.96 GB    132.59 GB    165.37 GB    44.5%   [****------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
+infmt_misc         0 KB         0 KB         0 KB     0.0%   [----------]
+joel/.gvfs         0 KB         0 KB         0 KB     0.0%   [----------]
+joel/Games     23.84 GB     171.9 MB     23.67 GB     0.7%   [----------]
+Media/pics     37.23 GB       4.2 MB     37.23 GB     0.0%   [----------]
+l/download     37.23 GB       4.2 MB     37.23 GB     0.0%   [----------]

I have been scratching my head with this one for a while and any help correcting this and recovering my lost disk space will be greatly appreciated. Thanks in advance!

Joel

---

