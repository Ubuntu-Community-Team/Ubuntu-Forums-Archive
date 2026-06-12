---
title: "first pictures gone. then recovered with jpegs turned png."
date: 2012-07-18
forum: Desktop Environments
---

### Post by tentoc on 2012-07-18
Hello all,

I have been digging around the net and ubuntu forums to find solution to this.
foremost, testdisk, photorec, scalpel..all tried. I got my photos back, with other problems I narrate below. 

the problem was: the photos folder on my external drive was gone, somehow deleted. 2500+ photos.
then I used testdisk and photorec (by the way, simultaneously, dont know if this had any effect on the result..) to recover them.

testdisk did not return this folder, nor the photos. instead it did show another folder that I deleted yesterday, and successfully restored it ( I did this just to see whether it worked.) 

photorec restored "all" photos in "re-cup" titled folders. I was informed later that this was typical of photorec, disregarding original names and folders. 
but this alone were ok. 
the problem I refer is that many of the recovered photos, which originally had jpeg formats, are now in png format, and more, are replaced by mere 2-3 images from a video I'd saved. so bizarre, these 2-3 still images from the video are what is to be seen in all these 100s of photos (the video might not even have been in the same folder, but in another "video" folder!).
in addition, many of the photos in jpeg format were reduced down to thumbnail size. curiously, others weren't. 

so this was the result with photorec.
 
when I tried scalpel after that, I received a folder full of octet-stream files named as jpg(-number) and gif(-number) (folder was created and auto-named as scalpel-output, as I gave the target folder name as "scalpel", as advised on the help website.) Can I do proceed anywhere further with these files? 
and, when scalpel completed the scan, though at the end there was the message that the target "scalpel" was not found. then I tried to create a folder with this name, this time it said the folder was not empty and that this was forensically not sound, and hence aborted.

foremost didnt work at all. when I used the commands as advised on the helping websites, the lines on terminal were filled with non-alphanumeric, crazy error symbols.

I tried to do above scans directly with the SD card of the camera, instead of the external drive, where the photos were saved. but testdisk strangely gave error like bad partition or sector..

I thought maybe I could recover all photos as original if I used one of the above methods other than photorec, but none hence seemed to work. I may possibly have done sth incomplete, too, as I use all these software for the first time. 

nor I could find any information on how to revert from png back to jpeg in cases like this. it's as if there are not many examples of such data corruption. 

as one more way to go, it comes to mind to scan the internal hard drive the same way.

I have no idea how this loss might have happened, and how I can avoid it.

would you have any suggestions what to do to recover the files?

Thank you very much for your time!
Regards,

---

### Post by David Andersson on 2012-07-18
> **tentoc said:**
> 
then I used testdisk and photorec (by the way, simultaneously, dont know if this had any effect on the result..) to recover them.

Simultaneous operation should be no problem, except maybe performance-wise. AFAIK they all save their findings in new folders. They don't mess around on the drive they are reading from. (I assume you directed them to save things on another drive than the drive they were analyzing.)

> **tentoc said:**
> 
photorec restored "all" photos in "re-cup" titled folders. I was informed later that this was typical of photorec, disregarding original names and folders. 
but this alone were ok. 

Most recovery programs ("foremost", "recoverjpeg", "photorec", "magicrescue", "scalpel", etc) works by recognizing headers of different file types. It search for patterns in the data on the disk and tries to deduce where the data of certain file types begin and end. They do not know about "file systems" that manages folder structures and the names and permissions of the files. They find the contents of files only and invent random file names for the recovered files.

"Testdisk" do know about file systems. I have not used it, but maybe it is the best option to recover files only from certain folders and with their original file names.

> **tentoc said:**
> 
the problem I refer is that many of the recovered photos, which originally had jpeg formats, are now in png format, 


The recovery programs actually found png-files then. They don't convert anything. Maybe some programs saved png thumbnails in a cache or something.

> **tentoc said:**
> 
and more, are replaced by mere 2-3 images from a video I'd saved. so bizarre, these 2-3 still images from the video are what is to be seen in all these 100s of photos (the video might not even have been in the same folder, but in another "video" folder!).

A video file consists of many images, to be shown quickly in a sequence. Typically every tenth or hundredth image are simply a jpeg compressed image inside the video file. Maybe the recovery program said, "hey, this looks like a jpeg image, lets recover it", and it was a jpeg image inside a video file. However, some recovery programs do recognize some video formats and would recover the complete video.

> **tentoc said:**
> 
in addition, many of the photos in jpeg format were reduced down to thumbnail size. curiously, others weren't. 


That is most likely thumbnail files that actually exists, or have existed, on the disk. The recovery programs do not resize anything. Many photo browsing programs and file browsers save thumbnails in hidden folders.

> **tentoc said:**
> 
foremost didnt work at all. when I used the commands as advised on the helping websites, the lines on terminal were filled with non-alphanumeric, crazy error symbols.


Strange. I think *foremost*, along with *photorec* and *recoverjpeg*, are the most competent and easy to use of those I have tried. What was the exact command line you used, or what helping website?

**After work**

After running a recovery program, the most work lies ahead. They have found images that have not been deleted and that does not need to be restored. And they have found old images that have been deleted before, that you do not want to restore. Sometimes they will find multiple copies of the same image. You have to find just the deleted images that you want to undelete.

In the package *recoverjpeg* there is a command *sort-pictures* that will organize images in sub folders by date. This requires the recovery program was able to recognize and recover EXIF-data with the images, and I think most of them are.

If EXIF-data was recovered, and depending on camera model, it may be possible to find out what number the image had in the camera, and then deduce what file name it had.

Would you like to participate in my poll, [http://ubuntuforums.org/showthread.php?t=2001222&page=4](http://ubuntuforums.org/showthread.php?t=2001222&page=4) , please?

---

