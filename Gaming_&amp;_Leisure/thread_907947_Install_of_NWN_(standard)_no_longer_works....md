---
title: "Install of NWN (standard) no longer works..."
date: 2008-09-02
forum: Gaming &amp; Leisure
---

### Post by senectus on 2008-09-02
I'm having some weird issues with installing NWN onto Ubuntu 8.04.

For starters the Icculus install client only sees cdroms mounted in standard mount points.. but for some reason Ubuntu 8.04 names the mount point of the CD after the name of the CD... So I can't get the Install client to see the cdrom properly..

Second it seems to skip right past the first and second install CD but it can see the third "Play CD" just fine... 

It's quite frustrating... 
Can anyone else replicate this? 
Do you have any advice for the renaming of the mount points etc? (or fixing them to one spot...

---

### Post by eragon100 on 2008-09-02
From the NWN installer FAQ:


	I mount my CDROM in some really obscure place.
A
	These are the mount points that will work without doing anything:

/mnt
/mnt/cdrecorder
/mnt/cdrom
/mnt/dvd
/media/cdrecorder
/media/cdrom
/media/dvd
/cdrom

If it is not listed here, you will have to set SETUP_CDROM before you run the installer.
eg. If you mount your CDROM under /mnt/cdrom0 then open a shell and type
export SETUP_CDROM=/mnt/cdrom0
./nwn_129_final.run

---

### Post by Perfect Storm on 2008-09-02
Try this: [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

Ignore installing ia32-libs if you're using Ubuntu 32-bit

---

### Post by senectus on 2008-09-02
> **eragon100 said:**
> From the NWN installer FAQ:


	I mount my CDROM in some really obscure place.
A
	These are the mount points that will work without doing anything:

/mnt
/mnt/cdrecorder
/mnt/cdrom
/mnt/dvd
/media/cdrecorder
/media/cdrom
/media/dvd
/cdrom

If it is not listed here, you will have to set SETUP_CDROM before you run the installer.
eg. If you mount your CDROM under /mnt/cdrom0 then open a shell and type
export SETUP_CDROM=/mnt/cdrom0
./nwn_129_final.run

That'll work for the first disc.. but when I put the second in it'll have a different mount point...

Artificial Intelligence :
That looks good, thanks... Will try it after work tonight.

---

### Post by senectus on 2008-09-02
That worked great.. thanks again :-D

---

### Post by senectus on 2008-09-02
ok.. now I'm freaked...

The Games launches and runs using the path /home/MyUsername/Desktop/.Games/nwn/nwn-launcher.sh

except that when I go browsing or ls -l in the .Games Directory... there is _nothing_ in it...

wtf is going on?!?!

---

### Post by Perfect Storm on 2008-09-02
Try 

ls -a instead

---

### Post by senectus on 2008-09-02
same result!

I also just tried to copy the whole ~/Desktop/.Games  Dir and everything behind it to ~/.Games and now I can see everything inside it...

Bloody strange...

---

