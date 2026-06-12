---
title: "Nautilus and file modified stamp [BUG ?]"
date: 2007-12-11
forum: Desktop Environments
---

### Post by oygle on 2007-12-11
I'm running Nautilus 2.20.0 on Ubuntu 7.10 , with all updates applied.

There were 56 updates today, took a while. Periodically, I copy a folder from Ubuntu computer over to a XP Pro computer, using Nautilus.

I noticed when I did this today, all the "date modified" timestamps were all set to the same on the XP box ??

All I do is copy the folder on Nautilus, then paste it into a Windows shared folder. In the past, the files all reflected the modified date/time from the Ubuntu computer, but now they all have the same timestamp, the time the files were copied over to Windooze XP.

Seems like a bug, maybe ??

---

### Post by oygle on 2007-12-12
Any clues ??

---

### Post by oygle on 2007-12-12
This does seem to be a bug shown [here]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/122302")

But what I don't understand is that prior to the updates yesterday, the modified time was okay when copying from Ubuntu/Nautilus ==> Win XP share  ??

---

### Post by oygle on 2007-12-21
Today I copied one file from Ubuntu to the XP computer, and, same problem, the modified datestamp for the file was changed to reflect the current date/time on the XP.

Then I copied the same file to a different HDD/partition on the same computer as Ubuntu, and the file modified stamp is okay, exactly the same as Ubuntu.   

So, is this an XP specific problem when copying to the XP share ?  I have checked the permissions on the XP share, and "guest" has full priviledges.

Any clues please ??

---

### Post by jetsam on 2007-12-21
Some additional details...

I get the behavior you describe, the timestamps are re-set, when I copy onto a Samba share in Nautilus through Places-->Network.  The modified timestamp is unchanged, though, when I use Nautilus to copy to the same share mounted with cifs.  

I think that narrows it down to a problem with Nautilus network browsing.  

A possible, if slightly complicated, workaround for you might be to mount your share with cifs and access it that way.

---

### Post by oygle on 2007-12-21
I don't use cifs, and although I have Samba running, there are no 'shared folders', and no Samba shares.

I have just been using Nautilus to browse to a share on the XP computer.

> **jetsam said:**
>  
I think that narrows it down to a problem with Nautilus network browsing.  


Yes, I think so, file timestamps aren't being changed on the same computer (Ubuntu), even though the HDD/partition I copied a file to was a Win95 HDD.

It would be good if I can find some way to run Nautilus from the command line, I'm not much of a Linux guru. There might be some helpful messages.

Have just browsed the network with Nautilus, to the XP share, and copied a file there with Mar 2006 date. Then pasted it on the Ubuntu box, and the date is fine, it hasn't been modified.

So, for me, the problem is only of one type, from Ubuntu to an XP share. It's only when the file is being written to the XP share, that the date gets set to current time.

---

### Post by oygle on 2007-12-24
Now I can't even read files on the Windows network, using Nautilus ??

However, I used Firefox and the address smb://computername/sharename/  worked just fine, I can read any file.

So, I guess it rules out Samba. Is there any other file browser, as a replacement for Nautilus ??

---

### Post by oygle on 2007-12-27
I have read through the [HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showpost.php?p=1174825&postcount=1") topic, and applied some minor changes.

From Ubuntu, I can see all the Windows shares, and also copy files from or to the XP computer, the only problem is the modified date, which causes some problems.

I haven't (as yet) setup a 'user' on the XP computer, and also setup that same user on Ubuntu. I can't see that it is necessary, as when Ubuntu/Samba copies files using Nautilus, the owner is 'guest' anyway, which is a valid user name on the XP box.

Do I _have to_ add a (Samba) user ??

I don't want to be able to browse the Ubuntu computer from XP, only the other way.

---

