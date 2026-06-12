---
title: "Serious flash drive transfer error!"
date: 2006-02-26
forum: Desktop Environments
---

### Post by anil_robo on 2006-02-26
(Caution: This is a relatively long post, so please be patient)

I converted my roommate yesterday to using Linux for his school homework. He was fed up with windows anyway so I installed Breezy on his laptop.

He downloaded several pdf articles from the web on his new Breezy desktop, and was going to print them from the library. So he cut and pasted all those pdf files in the usb flash disk, unplugged it and went to the library. In the library computer (which runs win xp pro) any of the files failed to show up - except one. He thought it may be an inter-OS incompatibility, and came back home to check.

He plugged in the USB flash drive again in his Breezy computer and the flash drive showed only one file. He checked his desktop - nothing was there. All the files should have been cut and pasted, but only one came in the flash disk. Where did the others go?

His project is due tomorrow and I'm terribly sorry for what happened. I think Breezy does not have good support for USB data transfer as yet.

His laptop is Sony Vaio FJ170 ([Configuration]("http://www.notebookreview.com/default.asp?newsID=2618&review=Sony+VAIO+FJ170")) and his flash disk is some unpopular Taiwanese company - but it has been working perfectly on windows for the last two years.

I had similar problems earlier - one of the friends wanted to see some of my videos. I transferred the DivX files (about 700 MB each) in my 1GB Verbatim flash drive, and handed it over to him. He later complained that the video got stuck about half-way through. He returned the flashdrive to me and I checked the md5sum. It was different from the file that I had on my hard drive. It means the data transfer over USB was faulty.

THIS IS SERIOUS! WOULD SOMEONE HAPPEN TO KNOW?
(And would someone post if they had similar experiences?)

---

### Post by madjinx on 2006-02-26
no no, it does support it. Heres the trouble, when you copy/paste or cut/paste onto a USB drive, it wont show the usually "trafsertime left' bar. You have to wait for the files to copy. Had he tried to unmount the drive proberly, it would have given him an eorror message saying it was still in use, ie still transfering data.

next time, tell him to wait a few minutes, and unmount it proberly.

---

### Post by Swiss on 2006-02-26
Properly! Did someone re-map your keyboard? ;)

---

### Post by madjinx on 2006-02-26
*cries*

i just woke up, leave me be!


ohh and the above statement of mine, was from personal experience.

---

### Post by Super King on 2006-02-26
I was weirded out by this same thing before. I'd transfer some stuff to my Lexar flash drive in Ubuntu, then just yank it out, plug it into a XP machine, and wonder, "hey, didn't I transfer those things?."

Before you disconnect your flash drive, go to Computer, then unmount it by right clicking on the drive (Unmount Volume).

---

### Post by Swiss on 2006-02-26
sorry...:)  Where do you live? Its 4:47 (PM) here.

---

### Post by madjinx on 2006-02-26
ohh its 5pm here too, its was a rough saturday night!

and IDK WHY anyone just pulls out a usb drive. you should ALWAYS unmount it first, even in Windows.

---

### Post by anil_robo on 2006-02-27
[quote=madjinx]no no, it does support it. Heres the trouble, when you copy/paste or cut/paste onto a USB drive, it wont show the usually "trafsertime left' bar. You have to wait for the files to copy. Had he tried to unmount the drive proberly, it would have given him an eorror message saying it was still in use, ie still transfering data.

next time, tell him to wait a few minutes, and unmount it proberly.[/quote]

1. Ideally it should show the file transfer window. If it doesn't, how am I gonna know when the transfer is complete? Do I have to guess?
2. All his files were cut and pasted in the flash drive. All the files do not exist on the original folder. Had he plugged out the flash drive when the transfer was  still ongoing, some of the files should still lie on the original folder on the hard disk - but that folder is empty. It means the file transfer was shown to be complete and ok, but when the flash drive was plugged in another computer, they were not there.

What the hell is going on here??? :(

---

### Post by RAOF on 2006-02-27
[QUOTE=anil_robo]1. Ideally it should show the file transfer window. If it doesn't, how am I gonna know when the transfer is complete? Do I have to guess?
2. All his files were cut and pasted in the flash drive. All the files do not exist on the original folder. Had he plugged out the flash drive when the transfer was  still ongoing, some of the files should still lie on the original folder on the hard disk - but that folder is empty. It means the file transfer was shown to be complete and ok, but when the flash drive was plugged in another computer, they were not there.

What the hell is going on here??? :([/QUOTE]
What's going on here is that the files were written to the write-cache.  That is, the file-operations completed successfully, but the kernel simply copied the data into memory (and was going to write the files out to the flashdrive in the background).  So, as far as everything but the lowest level of the kernel was concerned, your friends files had been written successfully.  Your friend then pulled out the flash drive (while the kernel was writing in the background) and only some of the data was finished writing to the flash drive.

You can get the same sort of behaviour under Windows by enabling "write caching" for removable drives.  It can make working on removable drives much faster (because if you're writing then reading stuff, you can read it even before it's finished writing - you can't read & write at the same time, and writing to flash drives is generally slow), but there's the problem that you can lose data if you don't unmount it cleanly.  You can do the same in windows, too, if you try hard enough :)

---

### Post by anil_robo on 2006-02-28
[quote=RAOF]What's going on here is that the files were written to the write-cache.  That is, the file-operations completed successfully, but the kernel simply copied the data into memory (and was going to write the files out to the flashdrive in the background).  So, as far as everything but the lowest level of the kernel was concerned, your friends files had been written successfully.  Your friend then pulled out the flash drive (while the kernel was writing in the background) and only some of the data was finished writing to the flash drive.

You can get the same sort of behaviour under Windows by enabling "write caching" for removable drives.  It can make working on removable drives much faster (because if you're writing then reading stuff, you can read it even before it's finished writing - you can't read & write at the same time, and writing to flash drives is generally slow), but there's the problem that you can lose data if you don't unmount it cleanly.  You can do the same in windows, too, if you try hard enough :)[/quote]

If that is the case, I'd recommend "write caching" to be disabled by default in Dapper. Can someone let the developers know this? Or tell me  how to inform them myself???

That could save a lot of such disasters! :(

---

