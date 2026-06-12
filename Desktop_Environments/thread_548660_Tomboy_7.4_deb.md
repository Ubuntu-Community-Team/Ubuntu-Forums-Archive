---
title: "Tomboy 7.4 deb"
date: 2007-09-11
forum: Desktop Environments
---

### Post by rogerdean on 2007-09-11
Hi folks
Any chance some kind soul could make up a deb of the latest Tomboy unstable release 7.4? Seems it now lets you sync your notes with some sort of online service, and that would be great for me. Am on track eventually to be able to do this stuff myself, but in the meantime...?
Would be very grateful
Allbest
Roger

---

### Post by rogerdean on 2007-09-12
or, even better, tell me how to do it myself? :)

---

### Post by jakev383 on 2007-10-07
I've got a good build of tomboy 8.0 on my system and would love to post the link for a deb, if someone can give me some tips on how to build a deb (I've only built RPMs in the past).
I'll look into this later this afternoon/early this evening if no one posts any tips for me before then.

---

### Post by ryno519 on 2007-10-07
> **jakev383 said:**
> I've got a good build of tomboy 8.0 on my system and would love to post the link for a deb, if someone can give me some tips on how to build a deb (I've only built RPMs in the past).
I'll look into this later this afternoon/early this evening if no one posts any tips for me before then.

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by rogerdean on 2007-10-07
Thanks very much jakev383 - no need from my side any more as I'm running Gutsy Beta which has it built in. Gutsy proper will come out in a few days, but it'd be good stuff to know anyway. I couldn't get that guide to work for me, but that surely me and not the guide...

---

### Post by jakev383 on 2007-10-07
Thanks for that link - it helped more than you know!
I built the .deb, but I'm sure I missed a few info fields in the .deb. I did install this on my laptop without incident though, so I can now sync my notes! (okay, as soon as I setup webdav....)
My site: [http://v2gnu.com](http://v2gnu.com)

The file download area: [http://v2gnu.com/filemgmt/viewcat.php?cid=7](http://v2gnu.com/filemgmt/viewcat.php?cid=7)

---

### Post by jakev383 on 2007-10-07
For others that may be looking for this.... I got WebDAV working and sync'ed my 2 computers. There's a few more steps to get it working under Feisty though.  Here's the steps:

```
sudo apt-get install sshfs libavahi-glib-dev libfuse-dev libneon26 libneon26-dev
modprobe fuse
sudo chmod +x /usr/bin/fusermount
sudo addgroup {your_username} fuse
wget http://noedler.de/projekte/wdfs/wdfs-1.4.2.tar.gz
tar xzvf wdfs-1.4.2.tar.gz
cd wdfs-1.4.2
./configure
make
sudo make install

```

I then did a reboot, and setup my WebDAV info and sync'ed all my notes. I have not tried sshfs for it yet, but the above does work for me on Feisty.

---

### Post by desperado666 on 2007-11-12
what webdav service you use? I cant sync my tomboy notes with who.hasfiles.com server

---

### Post by jakev383 on 2007-11-13
> **desperado666 said:**
> what webdav service you use? I cant sync my tomboy notes with who.hasfiles.com server

I run my own web servers and setup a DAV share there.

---

### Post by desperado666 on 2007-11-13
as far as i see wdfs does not support whohasfiles.com :(

---

