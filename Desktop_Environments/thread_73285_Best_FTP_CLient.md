---
title: "Best FTP CLient?"
date: 2005-10-08
forum: Desktop Environments
---

### Post by BIGtrouble77 on 2005-10-08
I've been using GFTP with marginal success.  It tends to crash with large transfers.  I also tried FireFTP(firefox extension) and that fails to authenticate to my XBOX.

So... I need a decent FTP client that'll let me log into my xbox and transfer over my emulators- which is about 50gigs.  SmartFTP in windows could handle that large of a transfer.

I'll try anything.  Does KDE have a default ftp program?  I'd preferably like something from the repositories.  Thanks,

-BT

---

### Post by zerhacke on 2005-10-08
This doesn't help, but gFTP doesn't cut it for me either.  While transferring about 20 gigs worth of mp3 files averaging 5 Mb a file, gFTP dropped nearly half the files.  Granted, it could have been the fault of the FileZilla FTP Server on the Windows machine, but Windows to Windows copies never do this.

---

### Post by KingBahamut on 2005-10-08
While it seems trite and nongraphical, I have for years used ncftp. 

I think there is a front end for it, but if not, its fairly simple and easy. 

apt-get install ncftp.

---

### Post by BIGtrouble77 on 2005-10-08
[QUOTE=KingBahamut]While it seems trite and nongraphical, I have for years used ncftp. 

I think there is a front end for it, but if not, its fairly simple and easy. 

apt-get install ncftp.[/QUOTE]

I snagged ncftp, but I'm having trouble transfering a directory with a bunch of sub directories.  Tried: get -R dosfiles /home/bob/dosfiles/

It just makes a blank files called dosfiles in my home directory.

I just wanna grab the contents of dosfiles and copy it to my home directory.

Thanks,
-BT

---

### Post by mcmuffy on 2005-10-08
I used iglooFTP a while ago and it seemed pretty full featured. The downside is that it is retail. I think a 30 day trial version can be downloaded though to test it.

[http://www.iglooftp.com/linux/](http://www.iglooftp.com/linux/)

---

### Post by aysiu on 2005-10-08
I, too, have been on the search for the "perfect" FTP client. For Mac, it's Cyberduck. For Windows, it's Filezilla. I tried gFTP and FireFTP, too. I also tried KBear and a few others. The best thing I've found for KDE, believe it or not, is just Konqueror. Type in the ftp address in the location bar and just drag-n-drop.

---

### Post by Zwack on 2005-10-08
Forgive me,,, But I use "ftp"

There are some things that graphical interfaces never do what I expect for... ftp is usually one of them.

If you want to grab the contents of a directory then mget  should work... You might need to create the directory structure locally... I tend to do something strange though...

If that is what I want then I zip or tar the directory, ftp it and then unzip/untar it...

Z.

---

### Post by drummer on 2005-10-08
[QUOTE=aysiu]I, too, have been on the search for the "perfect" FTP client. For Mac, it's Cyberduck. For Windows, it's Filezilla. I tried gFTP and FireFTP, too. I also tried KBear and a few others. The best thing I've found for KDE, believe it or not, is just Konqueror. Type in the ftp address in the location bar and just drag-n-drop.[/QUOTE]
The same can be done in Nautilus if you go to "Places > Connect to Server" and select the "ftp with login" option and put in the details. I haven't tried it with large amounts of files but it does work, albeit a little slow sometimes (could just be the server I'm using though)

---

### Post by BIGtrouble77 on 2005-10-08
[QUOTE=drummer]The same can be done in Nautilus if you go to "Places > Connect to Server" and select the "ftp with login" option and put in the details. I haven't tried it with large amounts of files but it does work, albeit a little slow sometimes (could just be the server I'm using though)[/QUOTE]
I can't authenticate to my xbox via nautilus, does is use passive transfers by default? (cause i'd need to turn it off if it does)  

Maybe i'll try konqueror, but it's a big transfer so i'll do that as a last resort.  I might also try the tar method, that sounds pretty simple...

---

### Post by pmj on 2005-10-09
[QUOTE=BIGtrouble77]I can't authenticate to my xbox via nautilus, does is use passive transfers by default? (cause i'd need to turn it off if it does)  

Maybe i'll try konqueror, but it's a big transfer so i'll do that as a last resort.  I might also try the tar method, that sounds pretty simple...[/QUOTE]
Are you by any chance using the FTP in the EvoX? I tried that and I could connect but I couldn't browse. Transfers didn't work properly either. My problems weren't the same as yours, but EvoX is old and crappy so I thought I'd ask.

I had better luck with the FTP server in XBMC. gFTP works just fine with it and I transferred about 10GB to my Xbox with it last week without any issues.

IglooFTP is pretty nice. It's pretty much a clone of FlashFXP and it supports queues, something that might be useful to you.

---

### Post by BIGtrouble77 on 2005-10-09
[QUOTE=pmj]Are you by any chance using the FTP in the EvoX? I tried that and I could connect but I couldn't browse. Transfers didn't work properly either. My problems weren't the same as yours, but EvoX is old and crappy so I thought I'd ask.

I had better luck with the FTP server in XBMC. gFTP works just fine with it and I transferred about 10GB to my Xbox with it last week without any issues.

IglooFTP is pretty nice. It's pretty much a clone of FlashFXP and it supports queues, something that might be useful to you.[/QUOTE]
Thanks for the info.  Yeah, I am using evox and the evox ftp.  I'll try out xbmc.  I don't know if it's evox, but the ftp transfers are sooooo slow.  I ended up transfering my dos files to a windows machine and it took forever to transfer about 2gb.

---

### Post by b34r on 2005-10-09
[http://pftp.sf.net](http://pftp.sf.net)

---

### Post by anatole on 2005-10-09
i used gftp for the first time, then learned how to use lftp, and i just love it... it may seem hard for the first time, because it's a command-line app, but that's what makes it cool and smart.

---

### Post by nix4me on 2005-10-09
The best ftp client I have found for Linux is SecureFTP.  Its java based and does a nice job.

Mark

---

### Post by sshetye on 2007-06-22
Funny. Konquerer works really nice and its quick too. Being a gnome user I didn't try it till now. gftp sucks by the way.

Also, remember that the xbox uses a modified fat16/32 system, called fatX. Several file names valid in ext2/3/ntfs will be truncated or be invalid on fatx. These will show up like this

<I'm approximating character length below>
<source>
looooooooooooooongfilename-1.bin
looooooooooooooongfilename-2.bin

<destination>
looooooooooooo.bin (last one overwrites any earlier)

I believe this shortening applies to entire paths too.

---

### Post by craigi on 2007-06-30
There's a beta version of FileZilla 3.0 which is now available for Linux.  Seems to be working great so far!

[http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=206762&release_id=513101](http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=206762&release_id=513101)

---

### Post by geovino on 2007-06-30
Fire ftp : an Add-on in Firefox browser. Works as good as any ftp I've used. Very smooth.:D

---

