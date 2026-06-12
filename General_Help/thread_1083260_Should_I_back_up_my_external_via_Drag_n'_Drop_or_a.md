---
title: "Should I back up my external via Drag n' Drop or an .iso? Ubuntu or in Windows?"
date: 2009-02-28
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-28
Alright I'm trying to make a back up of my entire system on a external HDD.

Now should I do this back up in windows or Ubuntu? (I want to be able to access all files in both OS)

Then should I just drag n' drop or should I make an .iso?

I need to make an .iso of my 40g OS HDD to keep on my 500g internal media.

Then I want to just have to back up the 500g internal on the 500g external.

---

### Post by taurus on 2009-02-28
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by PsychedelicWonders on 2009-02-28
So this is a program that copies everything for me?

What makes this program so special to download and use it vs. what is already on the comp?

So its best to do this in Ubuntu?

As mentioned, I want to be able to copy all files and access them both on windows and Ubuntu.

How/why is this better than an .iso?

---

### Post by PsychedelicWonders on 2009-03-02
bump

---

### Post by PsychedelicWonders on 2009-03-03
bump

---

### Post by PsychedelicWonders on 2009-03-04
So this is a program that copies everything for me?

What makes this program so special to download and use it vs. what is already on the comp?

So its best to do this in Ubuntu?

As mentioned, I want to be able to copy all files and access them both on windows and Ubuntu.

How/why is this better than an .iso?

---

### Post by PsychedelicWonders on 2009-03-05
bump

---

### Post by PsychedelicWonders on 2009-03-06
bump

---

### Post by PsychedelicWonders on 2009-03-08
I should state this, I want to continue to "update" this back up external from time to time, once a week, twice a month etc etc.

So I would want to do it in a way where it just updates the newest files and doesnt recopy everything again plus the new files.

Does that make sense?

So how should I execute backing up with my external?

---

### Post by PsychedelicWonders on 2009-03-11
> **PsychedelicWonders said:**
> I should state this, I want to continue to "update" this back up external from time to time, once a week, twice a month etc etc.

So I would want to do it in a way where it just updates the newest files and doesnt recopy everything again plus the new files.

Does that make sense?

So how should I execute backing up with my external?


Anyone?

---

### Post by MaxIBoy on 2009-03-11
Assuming your external is /dev/sda (make sure it's unmounted, too:)```
dd if=/dev/sda of=~/backup.img
```Do not type in /dev/sda1, because that wouldn't be a full disk image.


Remember that .iso files are ONLY FOR CDs AND DVDs!

---

### Post by PsychedelicWonders on 2009-03-11
> **MaxIBoy said:**
> Assuming your external is /dev/sda (make sure it's unmounted, too:)```
dd if=/dev/sda of=~/backup.img
```Do not type in /dev/sda1, because that wouldn't be a full disk image.


Remember that .iso files are ONLY FOR CDs AND DVDs!

I honestly cant remember how to tell if its unmounted or not?

so i want it to be unmounted though?

Is it best to back up via Ubuntu, or XP Pro?

I tried to copy or move the HDD I want to back up in Windows, and copy/move wasnt a highlighted option for some reason?

So I dont want to back up my HDD via an .iso?

I thought .iso was like a picture/snap shot of something?

Once the initial backup has been created, what is the easiest way to keep updating the back up external with out having to copy the entire HDD over again just to get to the new stuff?

---

### Post by x C0MMAND0 x on 2009-03-11
[http://www.macrium.com/](http://www.macrium.com/)

That allows you to "image" your HD, which basically makes an EXACT picture/snapshot of everything on your computer, exactly the way it is.

You can restore this image if you ever need to.  Check out the program called "reflect".  We use this at my office to make images for client computers all of the time before we do reinstallations, in case we need to pull some data or restore the old image.

Also, you are able to mount the image as an external drive, so that way you can restore individual files if needed.

---

### Post by MaxIBoy on 2009-03-12
> **PsychedelicWonders said:**
> I honestly cant remember how to tell if its unmounted or not?

so i want it to be unmounted though?Right click it in the side bar of your file browser, click "unmount volume," leave it plugged in.

> Is it best to back up via Ubuntu, or XP Pro?

I tried to copy or move the HDD I want to back up in Windows, and copy/move wasnt a highlighted option for some reason? I only know how to do this in Ubuntu.

> So I dont want to back up my HDD via an .iso?

I thought .iso was like a picture/snap shot of something? Iso is short for ISO9660, which is the filesystem used on most CDs and DVDs. You can name your disk image a .iso file, but the wrong programs will try to open it. .img files are generic disk images. In either case, you can mount the file using the "mount" command, as if you were mounting a hard drive.

> Once the initial backup has been created, what is the easiest way to keep updating the back up external with out having to copy the entire HDD over again just to get to the new stuff? For that, you should not create a disk image. Instead, use the program "rsync." 



If you want to use rsync, it's already installed by default. Keep the external drive mounted, then type "rsync -azvrP /media/disk/source /home/user/destination" (substitute the directory names with whatever you want.) Repeat that command whenever you want to sync again.

---

### Post by PsychedelicWonders on 2009-03-14
This Western Digital 500g external came with its own program for windows called WD Synch

If I use this WD Synch via windows, will it still also capture the files I've started and created in Ubuntu and then saved on the same HDD?

Right now the external is a Fat32 format.

I think I want NTFS correct?

So should I re-format this?

If I do, I would lose the WD Synch program wouldnt I?

So what should I do?

---

### Post by PsychedelicWonders on 2009-03-15
anyone?

---

### Post by PsychedelicWonders on 2009-03-21
> **PsychedelicWonders said:**
> This Western Digital 500g external came with its own program for windows called WD Synch

If I use this WD Synch via windows, will it still also capture the files I've started and created in Ubuntu and then saved on the same HDD?

Right now the external is a Fat32 format.

I think I want NTFS correct?

So should I re-format this?

If I do, I would lose the WD Synch program wouldnt I?

So what should I do?

bump

---

### Post by PsychedelicWonders on 2009-03-30
> **PsychedelicWonders said:**
> This Western Digital 500g external came with its own program for windows called WD Synch

If I use this WD Synch via windows, will it still also capture the files I've started and created in Ubuntu and then saved on the same HDD?

Right now the external is a Fat32 format.

I think I want NTFS correct?

So should I re-format this?

If I do, I would lose the WD Synch program wouldnt I?

So what should I do?

Anyone?

---

### Post by PsychedelicWonders on 2009-03-31
bump

---

### Post by sgosnell on 2009-03-31
Over the past weeks you could have tried syncing it and seeing if the Linux files were transferred to the Windows machine.  I have no idea, nor any interest, because I don't have a Windows box.  If you format the external drive, then yes, everything on it will be gone.  Make sure you have a backup.  There should be no need to reformat it, though, since both Windows and Ubuntu will recognize the FAT32 drive.  NTFS has overhead issues, and you really only need it if you have individual files larger than 4GB.

---

