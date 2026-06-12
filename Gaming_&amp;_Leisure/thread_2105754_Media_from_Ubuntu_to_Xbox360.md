---
title: "Media from Ubuntu to Xbox360????"
date: 2013-01-16
forum: Gaming &amp; Leisure
---

### Post by lferg on 2013-01-16
Hello everyone, I am having a bit of difficulty.  I have media on my Ubuntu machine (music, movies) that I want to play/watch on my Xbox 360.  With Windows, I would just copy the files to a USB thumbdrive, pop it in and watch the movie. When done, I would delete the file and load it up again.   This is the easiest/fastest way for me and I would like to continue but I am having trouble. When I copy the movie to my thumbdrive, my Xbox doesn't see it.  It "see's" the USB but doesn't like it and don't want to do anything with it.  Can anyone baby step me through this?

---

### Post by Lightning Dragon on 2013-01-16
Hello,

So files you drag, media like music and movies, does not show up on a USB when put into the Xbox? What file type is the movie? It can't be something the Xbox *doesn't* recognized. If it worked with Windows, it is because Windows and Xbox supports the same type of files. See this link;

[http://answers.yahoo.com/question/index?qid=20100918114700AAUDNAD](http://answers.yahoo.com/question/index?qid=20100918114700AAUDNAD)

If it is a file you played previously on Xbox, it might have gotten corrupted during the transfer to the USB.

---

### Post by sidzen on 2013-01-17
I think [*transmageddon*]("http://www.howtogeek.com/63011/how-to-convert-videos-with-transmageddon-in-ubuntu-linux/") may output in XboX format.  Check it out.

Or [Arista]("http://linuxappfinder.com/package/arista/")

---

### Post by lferg on 2013-01-17
They are avi and mp4 files. Dies it have something to do with the formating if the thumb drive itself? In the video player of the xbox, I see the drive but it's grayed out.  How should the USB drive be formatted?  The files came from my phone.  I ended up just connecting my phone to the x box but this isn't optimal.

---

### Post by Lightning Dragon on 2013-01-17
Let us see if it is a format problem or your media that is the problem. 

[http://cinelerra.org/footage/](http://cinelerra.org/footage/)

Download one of their test .avi videos, put it on the USB and then connect it to the Xbox after it has been shut off, and then tell us if they appear or not. 

If it does show up, please make sure *your* .avi is not using non-Xbox codecs for either audio or video. Try coverting the sound/audio to something AAC, MP3 and video to Mpeg,H.264.

If making sure the audio and video meets Xbox standards results into another failure, reformat the drive to FAT-32 after you back up all your data to a folder on a computer. This is what I did when my 16GIG Toshiba refused to work.

---

### Post by lferg on 2013-01-17
Trying to format the thumb drive results in the error, it's greek but I am going to start googling the parts and see if I can't figure out at least what it's saying

[B]Error creating file system: Command-line `mkfs.vfat -I -n "New Volume" "/dev/sdb1"' exited with non-zero exit status 1:
stdout: `mkfs.vfat 3.0.13 (30 Jun 2012)
'
stderr: `mkfs.vfat: /dev/sdb1 contains a mounted file system.
' (udisks-error-quark, 0)[/B]

---

### Post by dannyboy79 on 2013-01-17
i use ushare to share files within the ubuntu machine to my xbox. also, the usb drive should be formatted as fat32 and be no larger then 16gb, thats the largest thumb drive xbox will see.

---

### Post by lferg on 2013-01-17
Yes, I guess this is pretty much my problem, only thing is, nothing will allow me to format.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

That is one strange error. Try deleting the files on the USB, restart the computer and then try formatting it.

---

### Post by dannyboy79 on 2013-01-17
u can't format a drive that is mounted

---

### Post by Lightning Dragon on 2013-01-17
Hello,

I don't think he really has it mounted, though and that it is just messing up.

---

### Post by dannyboy79 on 2013-01-17
picture clearly shows it's mounted at /media/feel/newvolume

---

### Post by alan21276 on 2013-01-17
If your PC and Xbox are connected through the same router then you should consider using a upnp media server to stream all your music and videos direct rather than using removable media.

---

### Post by lferg on 2013-01-17
> **dannyboy79 said:**
> u can't format a drive that is mounted:KS

Thank you for this! It's the simple things that can frustrate us whom are new to Linux the most.  This is was golden advice.  I am formating now and will check to see if it works in an hour of so(when daughter gives up the Xbox) Thank you again!

---

### Post by Lightning Dragon on 2013-01-17
> **dannyboy79 said:**
> picture clearly shows it's mounted at /media/feel/newvolume

Oh, you are right. I did not see the image. I only saw the post with the error in bold.

---

