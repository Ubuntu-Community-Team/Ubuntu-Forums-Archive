---
title: "Help me create a boot CD please =p"
date: 2009-04-28
forum: General Help
---

### Post by alexj.wv on 2009-04-28
Hi, I am wanting to create a boot CD, I'm not trying to duel-boot or anything, I want to use Ubuntu as the sole OS on another PC. I copied the files to a disc but it does not work. I don't think I am making the CD correctly. Please help me:shock:

---

### Post by jbrown96 on 2009-04-28
[Here]("https://help.ubuntu.com/community/BurningIsoHowto") are the instructions to burn Ubuntu to a CD.

---

### Post by prem1er on 2009-04-28
Are you trying to create the cd in windows or ubuntu?

---

### Post by alexj.wv on 2009-04-28
I am creating the CD in windows vista. 

The instructions say:
Open Infra Recorder and click the 'Write Image' button...Select the Ubuntu CD image file you want to use, then click 'Open'.

I chose the Bootable_NoEmulation file, then burned it...

---

### Post by prem1er on 2009-04-28
Here is a tool that I use.  It is very simple and free it works with vista.  [http://www.freeisoburner.com/](http://www.freeisoburner.com/)

Where did you get the copy of Ubuntu that you want to burn?

---

### Post by alexj.wv on 2009-04-28
I downloaded InfraRecorder, and I downloaded ubuntu 9.04 off of the main ubuntu website.

---

### Post by prem1er on 2009-04-28
Try burning it with the one I suggested.  Are you getting an error while burning or is it just not booting from the disc?

---

### Post by alexj.wv on 2009-04-28
I really dont know which file to burn to the disc, the Bootable_NoEmulation file looks like its zipped but i cant unzip it, I basically have a folder with the 698mb download unzipped into it and need layman's instuctions

---

### Post by logos34 on 2009-04-28
you're looking for the .iso image--it must be inside.  Try [7zip]("http://www.7-zip.org/download.html") to unpack it

---

### Post by oldos2er on 2009-04-28
> **alexj.wv said:**
> I really dont know which file to burn to the disc, the Bootable_NoEmulation file looks like its zipped but i cant unzip it, I basically have a folder with the 698mb download unzipped into it and need layman's instuctions

 The *.iso file is the one you want to burn. It shouldn't be extracted.

---

### Post by alexj.wv on 2009-04-28
the boot file is zipped .img file..

---

### Post by prem1er on 2009-04-28
I am confused what that means.  Is the .iso file inside a compressed directory?  If you downloaded it from the Official Ubuntu page.  You just have an .iso file.  You need to select that file when burning it to a CD or DVD.

---

### Post by alexj.wv on 2009-04-28
I have folders: 
.disk
[BOOT]
casper
dists
install
isolinux
pics
pool
preseed

and

autorun
md5sum
README.diskdefines
ubuntu
wubi

I tried burning a data disk using just the windows utility, didn't boot, I downloaded InfraRecorder, is there a single file here that I need to "Write Image" in infrarecorder? I am still confused help

---

### Post by alexj.wv on 2009-04-28
the only image file is the bootable_NoEmulation file..

---

### Post by logos34 on 2009-04-28
Looks like the contents of the ubuntu install cd alright, but you should have downloaded it as a single .iso. How did you end up with the folders separate?

You need to gather them all up into an iso again, then burn to cd.  I'm not sure Infrarecorder will make the iso, but [ImgBurn]("http://www.imgburn.com/") can 'build' one and burn

---

### Post by prem1er on 2009-04-28
If you have a spare flash drive this could be much easier...and also run faster when you boot from it.  You got one?

---

### Post by networm1230 on 2009-04-28
boot cd are not hard to make here are the stap 1. you must download a image file from ubuntu or ather OS. stap 2 you must use a image burning software like [http://infrarecorder.org/](http://infrarecorder.org/) this is the same I used to make my cd (ubontu 8.04 live cd)
how to make a boot cd [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

hope it helps you

---

### Post by lisati on 2009-04-28
> **alexj.wv said:**
> I really dont know which file to burn to the disc, the Bootable_NoEmulation file looks like its zipped but i cant unzip it, I basically have a folder with the 698mb download unzipped into it and need layman's instuctions

> **logos34 said:**
> you're looking for the .iso image--it must be inside.  Try [7zip]("http://www.7-zip.org/download.html") to unpack it

Why the discussion about extracting the files?????? Just download the iso file, and burn it as a disk image! 

The link has already been mentioned but I mention it again: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by logos34 on 2009-04-28
> **lisati said:**
> Why the discussion about extracting the files?????? Just download the iso file, and burn it as a disk image! 

because alexxj said the file(s) are in some kind of zipped folder he can't unzip. It would have been quicker to just make an iso and burn it.  But by now it would have been better to re-download the darn thing

---

### Post by max_power on 2009-04-28
step 1. download ISO file from ubuntu
 (download [http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=http%3A%2F%2Fftp.ussg.iu.edu%2Flinux%2Fubuntu-releases%2F&arch=i386]("http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=http%3A%2F%2Fftp.ussg.iu.edu%2Flinux%2Fubuntu-releases%2F&arch=i386") )

step 2. download imgburn for windows  [http://dw.com.com/redir?edId=3&siteId=4&oId=1770-20_4-0&ontId=20_4&spi=1971427609740a3b8684c9dc3492adcf&lop=btn&tag=tdw_dlicon&ltype=dl_dlnow&pid=11019723&mfgId=6305991&merId=6305991&pguid=YRkiVAoPjAEAAHxGcgEAAADB&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-20_4-10847481.html%3Fspi%3D1971427609740a3b8684c9dc3492adcf]("http://dw.com.com/redir?edId=3&siteId=4&oId=1770-20_4-0&ontId=20_4&spi=1971427609740a3b8684c9dc3492adcf&lop=btn&tag=tdw_dlicon&ltype=dl_dlnow&pid=11019723&mfgId=6305991&merId=6305991&pguid=YRkiVAoPjAEAAHxGcgEAAADB&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-20_4-10847481.html%3Fspi%3D1971427609740a3b8684c9dc3492adcf")


step 3. install imgburn

step 4. run imgburn and select "Burn image to disc"

Step 5. locate the ISO file and burn it.

Burn the disc a slow burn speed or you might have problems

---

