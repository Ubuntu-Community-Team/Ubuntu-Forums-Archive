---
title: "tenfolded disk usage after sftp-transfer of photos (mtp-Handy connection)"
date: 2021-11-04
forum: Desktop Environments
---

### Post by mue.de on 2021-11-04
Hi guys,

I'm encountering a problem when trying to copy files (photos) from my Handy (SM-A540, mtp:-protocol) to my 'server' (Laptop, sftp-filesharing).
As seen in the hard-copy the occupied disk-space is ten-folded at the target disk.

Origin:
> [FONT=monospace][COLOR=#54ff54]**muelux@LT76A-T430**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsb_release -dc [/COLOR]
Description:    Ubuntu 20.04.3 LTS 
Codename:       focal 
[COLOR=#54ff54]**muelux@LT76A-T430**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ uname -r [/COLOR]
5.4.0-89-generic
[/FONT]

Destination:
> [FONT=monospace][COLOR=#000000]muelux@LT71A:~$ lsb_release -dc [/COLOR]
Description:    Ubuntu 16.04.7 LTS 
Codename:       xenial 
muelux@LT71A:~$ uname -r 
4.4.0-171-generic 
muelux@LT71A:~$
[/FONT]

Any suggestions?

Thanks in advance for any advice.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289424&stc=1[/IMG]

---

### Post by TheFu on 2021-11-04
Very odd.

What does **du -h** or **ls -l** show?

Could multiple images be added automatically by some processing?  For example, some software will put thumbnails into the EXIF data, which will make for larger files.  I don't think this is possible over the sftp protocol. That's just moving bits from A ---> B.  But who knows what the MTP implementation on the "Handy" does?  Does that camera put RAW images inside the JPG files?   [https://www.photo.net/discuss/threads/embedded-jpg-in-the-raw-file.500315/](https://www.photo.net/discuss/threads/embedded-jpg-in-the-raw-file.500315/) says that different cameras embed the JPG into the RAW image, but nothing about the other way around.  Does "JPEG-Bild" mean something specific? If you look at the EXIF data in the files, are there any hints for processing performed?

For my cameras file sizes are typically 1-6 MB, depending on the subject complexity. They don't do "raw".  

I've not noticed this with any of my Android devices using MTP.  To get files off my cameras, I pull the SDHC card and insert it into a slot on the laptop/PC and copy the files off directly for processing before pushing them into a web-based gallery app.

---

### Post by mue.de on 2021-11-04
Thanks for your answer :-)
The 'du -h' shows this for the Import-Folder (on the Destination-Laptop), the shown '.jpg'-image is the highlighted from my first post:
> muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy/79BA_Ewis_Hdy/Camera$ ll 20210404_135049.jpg 
-r-xr-xr-x 1 muelux muelux 52706960 Apr  4  2021 20210404_135049.jpg*
[EMAIL="muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy"]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy[/EMAIL]/79BA_Ewis_Hdy/Camera$ du -h
5,1G    .
[EMAIL="muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy"]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy[/EMAIL]/79BA_Ewis_Hdy/Camera$ 


The size of the Handy Folder is 1.7G (424 files of almost (4...7)MiB, as per Dolphin, i don't know the real address for the 'du'-command ('/var/run/user/1000/....?')
The Camera is a simple Samsung Handy (SM-A520F, 12MP-Camera), it doesn't store 'raw'-Format pictures.
The 5.1G disk-space is the occupied space for 51 files, that were transmitted; then i stopped the transmission.

It looks to me, as if the files were transported block-by-block, where the block-sizes of the target (4096B) is eight-times larger then the block-size of the origin (512B).

---

### Post by TheFu on 2021-11-04
Well, a 4KB block size would waste no more than 3.9999KB, right?
If they are block for block copies, that seems odd, but you can try copying the files (don't mv)  to another directory so the full 4096b will be used in each block, except the last 1.  Interesting.  This is effectively a defrag.  Then, after the the copy of all files is complete, remove the old directory.

I have doubts this is truly the cause, but MTP and GUIs can do odd things.

---

### Post by mue.de on 2021-11-04
Well, i mean, for every 512B block of the original file there is one 4K-block on the destination disk allocated, so the occupied space is seven-times larger.
I tried copying one of the files at the target disk with dolphin: it results in an 'internal error' (see below).
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289426&stc=1[/IMG]

With ''FreeFileSync'' i managed to get a copy of the folder, it's 1:1 size.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289427&stc=1[/IMG]

---

### Post by TheFu on 2021-11-04
Yes, I understood that.

What I'm suggesting that you login via ssh to the sftp-server, go to the directory with the files, create a subdir (temporary) and copy the files into it. This is troubleshooting to determine the real issue still.  If the copied files stay huge, then we know 1 thing.  If the copied files shrink back to about 4MB, then we know it is the MTP causing the issue.  I wouldn't assume sftp is involved at all, since it is used millions of times every hour without this side-effect.

Please humor me. Don't use the GUI.

---

### Post by mue.de on 2021-11-04
Ok, i tried that; the size of the copied files stays 1:1.

> [FONT=monospace][COLOR=#000000]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy/79BA_Ewis_Hdy/Camera$ cp -av . ./tst  [/COLOR]
'.' -> './tst' 
'./20210331_154330.jpg' -> './tst/20210331_154330.jpg' 
'./20210403_181643.jpg' -> './tst/20210403_181643.jpg'
[...
...]
[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy/79BA_Ewis_Hdy/Camera$ du -h tst [/COLOR]
5,1G    tst[/FONT][/FONT]

---

### Post by TheFu on 2021-11-04
And if you copy 1 file?
```
$ cp     20210331_154330.jpg      ./tst/
```
I've never done a directory copy using . before.  I tend to use *g or rsync.
Simplify and test. Repeat until it isn't possible to simplify any more.

Next would be to pull the storage out of the device, insert it into the computer and see if the files are reported different sized and if the copy (1 file) stays the same or not.  That would remove the MTP aspect.

---

### Post by mue.de on 2021-11-05
Here the results of the copy-test:
> [FONT=monospace][COLOR=#000000]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy/79BA_Ewis_Hdy/Camera$ cp 20210331_154330.jpg ./tst/ [/COLOR]
[EMAIL="muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy"]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy[/EMAIL]/79BA_Ewis_Hdy/Camera$ ll 20210331_154330.jpg  
-r-xr-xr-x 1 muelux muelux 4067159 Mär 31  2021 [COLOR=#54ff54]**20210331_154330.jpg**[/COLOR][COLOR=#000000]* [/COLOR]
[EMAIL="muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy"]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy[/EMAIL]/79BA_Ewis_Hdy/Camera$ ll ./tst/20210331_154330.jpg  
-r-xr-xr-x 1 muelux muelux 4067159 Nov  5 21:05 [COLOR=#54ff54]**./tst/20210331_154330.jpg**[/COLOR][COLOR=#000000]* [/COLOR]
[EMAIL="muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy"]muelux@LT71A:~/Bilder/_Photo_Import_temp.Hdy[/EMAIL]/79BA_Ewis_Hdy/Camera$ 
[/FONT]
To pull the storage out of the device doesn't matter, since these photos are on the internal storage.
To clarify the circumstances: copying (with USB-cable connected) from the Handy over mtp:-protocol to the local laptop doesn't make any problems!
The problem occurs only when copying the files from the handy over sftp:-protocol to the server.
The screenshot shows the actual copy of this file from Handy to local disk (mtp-connection over usb-cable, no sftp:-protocol involved, per GUI, dolphin) 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289428&stc=1[/IMG]

---

### Post by TheFu on 2021-11-05
Great that you solved it, but I don't understand. That's fine. I don't need to.

Please mark the thread as "SOLVED" using the thread tools button, to help other members of the community.

---

### Post by mue.de on 2021-11-06
Sorry, I can't really mark the thread as solved, since the issue isn't solved: I just said, that copying over 'mtp'-protocol to the** local laptop** is ok.
The problem of the growing file-space (up to 8-times larger than the original file-size) occurs, when i try to copy the files directly to the server (over 'sftp'-protocol).
I can use the work-around of local copying first, but that behavior is a malfunction (of 'sftp', of the different Ubuntu-Versions, of erroneous en-/decryption...?, of the different file-systems (vfat vs. ext-4)) .
I think, i have to new-install the Ubuntu system of the Server, since it is outdated ('Xenial').
That means a lot of work, since there runs an apache2-Web-Server with my *Moin-Moin* Wiki...

But thanks for your suggestions and your time!

---

