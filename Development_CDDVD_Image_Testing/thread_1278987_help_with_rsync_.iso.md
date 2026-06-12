---
title: "help with rsync .iso"
date: 2009-09-30
forum: Development CD/DVD Image Testing
---

### Post by stinger30au on 2009-09-30
i downloaded an iso of karmic 9.10 386 iso a few days ago and now i want to rsyc it to get the latest files

so i followed the instructions here

[https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

basically i fired up shell and went to the directory i have got the iso saved in to and ran copy/paste this

rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso


when i do this i get this out put

receiving file list ... 
1 file to consider
-rw-rw-r--   731252736 2009/09/30 05:40:02 karmic-desktop-i386.iso

sent 115 bytes  received 82 bytes  43.78 bytes/sec
total size is 697.38M  speedup is 3711942.82

now what???
is that it??
is there any thing else for me to do or is it all up to date?

---

### Post by lavinog on 2009-09-30
I would check the md5sum, but that should be all.  Like the page says, rsync only updates the changes and the changes are pretty small between updates.

---

### Post by stinger30au on 2009-09-30
> **lavinog said:**
> I would check the md5sum, but that should be all.  Like the page says, rsync only updates the changes and the changes are pretty small between updates.

the md5 sum is different

if i type this  in to shell i get
md5sum karmic-desktop-i386.iso 

9115da558cb90b0c0ba994b02cc51b65

if i look at the md5sum for the iso from the web site i get this
c07bc8085ab72e25b9372db4a2f6f784 *karmic-desktop-i386.iso

---

### Post by stinger30au on 2009-09-30
out of interest i created a new directory and if i go in to the directory via shell and run this

rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso


i get this output

receiving file list ... 
1 file to consider
-rw-rw-r--   731252736 2009/09/30 05:40:02 karmic-desktop-i386.iso

sent 115 bytes  received 82 bytes  43.78 bytes/sec
total size is 697.38M  speedup is 3711942.82


so clearly the  rsync command is doing nothing to update my pc. surely there is more to it then this

---

### Post by boblemur on 2009-10-01
hey again, if you read the website carefully you will see there is a subtle difference.

here is there command:
```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso .
```

here is your command:
```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso
```

almost identical, the problem with yours is you are missing the . on the end of the command, now in this case that is actually the destination for the saved file, because as you may know "." means your current directory so.
```
cd ~/Desktop/
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso .
```

the first will change to the desktop, and the second will download the iso to the folder . which you can find what . is by using 
```
pwd
```
and it will tell you(for me):
```
$ pwd
/home/nick/Desktop
```

you can equally put:
```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso ~/Desktop/
```

if you find the . notation unclear.

so basically: you forgot the destination parameter so when rsync gets the information off the server about which files it needs to copy, it gets that and then finishes because there is no more locations to download them to.

ps: congrats on getting the evolution thing to work hopefully it wont cause you anymore issues :)

---

### Post by stinger30au on 2009-10-02
ah ha!!!

just a small

.


makes the world of difference!!

THANKS!!

ps...

im glad i got my evolution email sorted too

i was damn near in tears last night cos the backup was not working and giving me issues i thought i had 2 hdd's dies at once

lucky it wasnt the case

---

### Post by technicallygeek on 2009-12-03
I was having problems with the rsync command as well. I setup a folder for the images I wanted to test I would cd to that directory and try the command without the trailing .

will this work for updating ubuntu-9.10-desktop-amd64.iso with the daily lucid images? or do I need to download a different iso if so which iso?

---

