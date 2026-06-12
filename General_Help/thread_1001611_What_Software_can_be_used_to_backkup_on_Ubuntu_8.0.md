---
title: "What Software can be used to backkup on Ubuntu 8.04!"
date: 2008-12-04
forum: General Help
---

### Post by kieranchiru on 2008-12-04
Hi All,

Can any tell me what software can be used to backup on ubuntu 8.04, 

Backup device : LTO3
Disk          : RAID5


For example on Window's OS we are using Symantic Software for backingup,
with similar backup device.

Any help would be greatly Appreciated

Cheers
Kieron  :0)

---

### Post by beginnerslinux.org on 2008-12-04
Hi,

Take a look at mondo/mindi

[http://packages.ubuntu.com/gutsy/mondo](http://packages.ubuntu.com/gutsy/mondo)

---

### Post by mkvnmtr on 2008-12-04
There are a lot of different back up programs. I guess the best thing is to go to the package manager and put "back up" in the search box. Then read up on the different programs. When you find one or two that you think you will like come back to the forum to ask if anyone has experience with those programs. Or you could just install check them out and if you don't like one just uninstall.

---

### Post by gabril on 2008-12-04
check out apttocd in the apt repository its a lifesaver for your apt apps!:D

---

### Post by stevebond001 on 2008-12-04
Hi
I would strongly suggest using Quickstart ([http://quickstart.phpbb.net](http://quickstart.phpbb.net))

Amongst a lot of other things, it provides a gui for taking both data backups and images.

It's the doggy's doodaa's in my opinion.

Hope this helps

---

### Post by eternalnewbee on 2008-12-04
> check out apttocd in the apt repository its a lifesaver for your apt apps
Couldn't find it...

---

### Post by glotz on 2008-12-04
I think he meant aptoncd.

One solution is [http://www.partimage.org/](http://www.partimage.org/)

---

### Post by eternalnewbee on 2008-12-04
> I think he meant aptoncd.
Thanks glotz.

---

### Post by spcwingo on 2008-12-04
You could also use remastersys to backup to CD/DVD.

---

### Post by scouser73 on 2008-12-04
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by Ellaine on 2008-12-04
I've been using Acronis True Image in windows for years. The boot CD for True Image works just fine in Ubuntu 7.04 thru 8.04. I put the image .tib on a second drive from Ubuntu and ammend when updates are installed. Works great and only takes a few minutes to restore after I make mistakes like putting in IE-6. I do like Opera.):P

---

### Post by deipert on 2008-12-05
Are there any issues using the boot Acronis CD for Windows to image the ext3 partitions?  Has anyone actually tried a retore with Acronis Windows?

What does the expensive Acronis Linux Server backup do?  This appears to run under Linux while it is up and running and does incremental backups.

While a boot image is better than nothing, I prefer a functional scheduled backup with incrementals.  I am using Acronis Echo Workstation for Windows and looking for an equivilant in Ubuntu  or something close to it.  Any ideas?

---

