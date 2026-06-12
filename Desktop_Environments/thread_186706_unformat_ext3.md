---
title: "unformat ext3?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by jpgeerets on 2006-06-02
hi folks,

last night i tryed to update my kubuntu from breezy to dapper drake.....
with synaptic -> this went wrong.
i get trouble with my X-server.

so i downloaded an install cd.
during install i could choose manualy manage my partitions on disk.
so i choose: 
- hda2 = /swap
- hda5 = /home
- hda6 = /

in /home are all my user files, pictures, administration, etc etc. at least 1 year of work gone...](*,) 

during install i guess i have the mistake to tell hda5 = / and hda6 = /home.
so....
al my user files are gone....
and... ofcourse no recent backup.

now im thinking how to unformat the hda5 so i can get back my user files.
then i will install kubuntu again, that's no problem, if i can save my /home files......

hda3 is ntfs.... this still works..... (winxp)

i hope someone can give me good advice on how to handle to get back my important user-data.

thanks in advance!!!

Jean-Paul

---

### Post by az on 2006-06-02
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Download and build foremost (the version in the repositories is too old.)

It can recover some or all of your files from the filesystem.  Run it from a live cd and create a filesystem on a free partition to dump you files there.  Boot the live cd, download foremost and install build-essential and then compile foremost.

---

### Post by Rackerz on 2006-06-02
[QUOTE=azz][http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Download and build foremost (the version in the repositories is too old.)

It can recover some or all of your files from the filesystem.  Run it from a live cd and create a filesystem on a free partition to dump you files there.  Boot the live cd, download foremost and install build-essential and then compile foremost.[/QUOTE]

So this can get back some files, even after a format?

---

### Post by jpgeerets on 2006-06-02
hi azz,

tnx for you advice!
i have installed it.
read the man twice.
but, still i dont get how to get my data back of my formatted partition.
i hope you can give me an example....

tnx in advanced!!!

Jean-Paul

---

### Post by az on 2006-06-02
mount your free partition somewhere and create a directory there.  Let's say you called it "saved"

sudo mount /dev/sda1 /mnt

sudo mkdir /mnt/saved

then you would run foremost on your borked partion:

sudo foremost -i /dev/hda5 -o /mnt/saved
 

That's it.

---

### Post by jpgeerets on 2006-06-05
hi azz,

i get a lot of my files back.
but, only the known.. like jpg, bmp, etc etc.
im also looking for pef files --> raw picture format of pentax digital camera.

i guess i can use an option to do this.
i will try it again....

tnx!

---

