---
title: "partitioning, file system and software raid"
date: 2005-10-21
forum: Desktop Environments
---

### Post by wimalwimal on 2005-10-21
hi,

i am a newbie to linux and glad that i was given a ubuntu cdrom by one of my friends while looking for a flavour of linux.

i am in the process of installing a server which will host a postgresql database server with php and apache.

i have several queries;

1.
as per the knowldge i have gathered past few days, i can create any number of partitions on a disk but swap and boot are mandetory. i have to mount each partition in a folder to be accessible from the file system since linux uses a file system insted of drive letters used in windows.

for an instance, for a home directory what is the benefit having a separate partition and mounted it as 'home' other than having folder in the root partition called 'home'

2. 
is it possible someone to guide me step by step to software raid (raid 1) since i have 2 scsi hdds of 73gb each.

3.
has anyone done any hardware raid with 39320A and using ubuntu. if so do you have drivers.

4. 
i am not going to connect this server to internet, therefore please guide me to use apt-get with cdrom, usbdisk, floppy.

5. 
suppose a partition is mounted as 'data' and it goes out of space for new data,
a) how to allocate free blocks from another partition.
b) attach new disk and link that partition to the 'data'

---

### Post by odin on 2005-10-21
[QUOTE=wimalwimal]hi,

i am a newbie to linux and glad that i was given a ubuntu cdrom by one of my friends while looking for a flavour of linux.

i am in the process of installing a server which will host a postgresql database server with php and apache.

i have several queries;

1.
as per the knowldge i have gathered past few days, i can create any number of partitions on a disk but swap and boot are mandetory. i have to mount each partition in a folder to be accessible from the file system since linux uses a file system insted of drive letters used in windows.

for an instance, for a home directory what is the benefit having a separate partition and mounted it as 'home' other than having folder in the root partition called 'home'

2. 
is it possible someone to guide me step by step to software raid (raid 1) since i have 2 scsi hdds of 73gb each.

3.
has anyone done any hardware raid with 39320A and using ubuntu. if so do you have drivers.

4. 
i am not going to connect this server to internet, therefore please guide me to use apt-get with cdrom, usbdisk, floppy.

5. 
suppose a partition is mounted as 'data' and it goes out of space for new data,
a) how to allocate free blocks from another partition.
b) attach new disk and link that partition to the 'data'[/QUOTE]

I'll try to help with some things.

1-The benefit of having /home ,using your example, in a different partition is that if your system crashes then you would still have the documents of all your users.

2-About the raid question, I cant help you a lot with that but I found this howto in the ubuntu wiki that may help you. The link is: [https://wiki.ubuntu.com/Installation/RAID1?highlight=%28raid%29](https://wiki.ubuntu.com/Installation/RAID1?highlight=%28raid%29)

I cant tell you much more but these questions are things I am interested in so I'll also do some research.If I find out something I'll post it here

---

