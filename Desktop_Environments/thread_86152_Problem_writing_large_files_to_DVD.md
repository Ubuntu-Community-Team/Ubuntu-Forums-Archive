---
title: "Problem writing large files to DVD"
date: 2005-11-04
forum: Desktop Environments
---

### Post by getaceres on 2005-11-04
Hi. I'm trying to backup a file (>4GB) that I've got in my hard disk to a DVD. The problem is that when I try to write it with k3b it ends without writing anything and without giving me an error.
Looking at the debug info, I've found this:

/usr/bin/X11/mkisofs: Value too large for defined data type. File /home/jose/video.mpg is too large - ignoring

I'm using a UDF filesystem and the person who gave me the original file, writed it with Nero without a problem.
Is there a way to remove that limitation? If so, how?

---

### Post by stimpack on 2005-11-05
bump

Ive had so many different unrelated problems with files > 4G

---

### Post by getaceres on 2005-11-06
It's a shame I had to reboot to Windows and use Nero to burn my CD. It didn't have any problem to burn my large file.

---

### Post by Princey on 2005-11-06
[QUOTE=getaceres]

I'm using a UDF filesystem and the person who gave me the original file, writed it with Nero without a problem.
Is there a way to remove that limitation? If so, how?[/QUOTE]

It would be interesting to note that Ahead Nero has released a linux version of Nero. I understand it's free until November, I haven't checked it out seeing I got the beta version last month. I have installed it and it works pretty fine. Might want to give it a shot.

---

### Post by Takis on 2005-11-07
Not like I could possibly ever answer this question, but for a bit of clarification, when you say "> 4GB" do you mean "4GB < size < ~4.3GB" (so it should fit on a single-layer DVD) or do you mean it's gigantor, and you're trying to burn dual layer?
If the latter, I guess we could take this as a sign that K3B might not be 100% at dual-layer burning just yet.

---

### Post by getaceres on 2005-11-07
[quote=Takis]Not like I could possibly ever answer this question, but for a bit of clarification, when you say "> 4GB" do you mean "4GB < size < ~4.3GB" (so it should fit on a single-layer DVD) or do you mean it's gigantor, and you're trying to burn dual layer?
If the latter, I guess we could take this as a sign that K3B might not be 100% at dual-layer burning just yet.[/quote]

No. It was a 4.2 GB file. It fits in a single layer dvd media.

---

### Post by Takis on 2005-11-07
In that case I've got nothing. :(

---

### Post by SWAT on 2005-12-06
[On this site](http://lantech.geekvenue.net/chucktips/jason/chuck/1077301682/index_html) I found this remark "updating mkisofs to the latest development release (2.01a27) worked for me too."
I think I'm going to try it too.

---

### Post by HermanAB on 2005-12-06
Hmm, run the commmands manually to figure out what is going on.  The trouble with any GUI is that they don't give you proper error messages - so a GUI is only good when it works - useless for debugging.

K3B and others are GUI front ends to mkisofs and cdrecord.  So a quick manpage read and you'll be on your way.  The problem can be with either mkisofs or cdrecord.

---

### Post by SWAT on 2005-12-07
[QUOTE=HermanAB]Hmm, run the commmands manually to figure out what is going on.  The trouble with any GUI is that they don't give you proper error messages - so a GUI is only good when it works - useless for debugging.

K3B and others are GUI front ends to mkisofs and cdrecord.  So a quick manpage read and you'll be on your way.  The problem can be with either mkisofs or cdrecord.[/QUOTE]
It's definately with mkisofs. I tried a mkisofs -udf... and it didn't work. The message was that the file was just too large (4.1GB or something). Somehow this relates to a strange bug in mkisofs, which is part of cdrtools. Some versions seem to work and some don't with files larger than 4GB. I didn't test anything yet (got a lot of work to do)

---

### Post by UbuXian on 2006-03-11
I am having this problem as well as I try to do a backup of data to DVD.  I have used KDar to create 4.3 G files for burning to DVD.  I am running Breezy on a PC with an NEC ND-2510A DVD drive.  I have used Nautilus burning and Gnomebaker with similar results.  Burning of smaller files works fine.  Here is a log of the problem from Gnomebaker.  The problem also occurs trying to just write an iso.

INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
mkisofs: Value too large for defined data type. File xxxxx.dar is too large - ignoring
Total translation table size: 0
Total rockridge attributes bytes: 169
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
181 extents written (0 MB)

Here's what I have discovered so far.  GUI burning front-ends use mkisofs to make an ISO file that is then burned to the disc.  mkisofs had problems with file sizes over 2 Gb per a google search.  My suspicion is that this bug has since been fixed, but I 'm not certain.  Next, I found some discussion about Fat32 file-size restrictions of 4 Gb creating problems.  Lastly, the latest version of Gnomebaker (0.5.1) per the sourceforge homepage) has a fix that will "attempt to enable large file support (>2GB) using AC_SYS_LARGEFILE).  I have not tried downloading that yet since I prefer to stick to the repositories.  

I'm not sure what to try now, though I am thinking of attempting with k3b.    One tip I can offer is to simply try to create an iso while trying to get this to work, thereby avoiding DVD coasters.    If you can create the iso, you should be able to burn the disk.

I am a little surprised that there has not been more mention of this in the forums.

BTW, thank you to everyone for all of the help in the forums.  I have used them extensively as a lurker to get my system going and to learn about Ubuntu.

---

### Post by Princey on 2006-03-11
I'm not sure if this will help, but is DMA enabled for your burner? I use nerolinux to burn my DVD's and even then I had to enable DMA support for my burner. Once again, I'm not sure if this will help you in your particular case.

---

### Post by Sandu on 2006-06-16
If you have free disk space -- make ISO-file, first. Then right-click this file and burn it to DVD.

---

### Post by kolavar on 2007-07-15
The reason you're unable to burn 4GB+ size files to a DVD is because the disc image creator (mkisofs) makes an ISO9660 filesystem. The limits of using the ISO9660 standard on a disc includes not being able to have files greater than 4GB in size, short disc labels and a restricted set of characters in disc labels. If you were to use mkudffs, to make the disc image, you could probably burn it with growisofs without any problems, but I haven't ever tried it before.

Sadly, the only solution GUI I've found is to burn files using ImgBurn under Windows, with it configured to use UDF. Maybe someone with some terminal know-how will come along and enlighten us.

---

### Post by Fraoch on 2007-08-21
Unfortunately GnomeBaker and Brasero are completely useless here, they both give the "value too large error".  But I did eventually get this to work in a roundabout way.  I'm burning backups, which I produced in DVD-sized chunks using this:

[http://www.bluehaze.com.au/unix/cdbkup.html](http://www.bluehaze.com.au/unix/cdbkup.html)

which made files called "<date, time>.cpio.bz2.000" and .001 etc.  I did manage to burn them to DVD+RW by following these instructions:

[http://blog.unixlore.net/2007/02/creating-large-2gb-dvd-backups-under.html](http://blog.unixlore.net/2007/02/creating-large-2gb-dvd-backups-under.html)

I thought I was stuck here since my DVD now does not have a file system and can't be mounted, browsed or accessed.  The author's example of decompressing it assumes it's a .tar, but it isn't, so I thought I had a DVD+RW full of data I couldn't access.  I had thought of formatting it UDF and didn't get anywhere with that, but finally that blog post made me realize that while the DVD drive can't be mounted, it can be copied like one big file:

```
cp /dev/hdc /tmp
```

However now I might be stuck.  The resulting copy is just named "hdc", no extension, and when I rename it the same as the original, diff says they differ (immediately, without really thinking about it).  The file size is the same, and I'm hoping diff is just complaining about modification date/time or something silly like that, but it is worrisome.:(

---

