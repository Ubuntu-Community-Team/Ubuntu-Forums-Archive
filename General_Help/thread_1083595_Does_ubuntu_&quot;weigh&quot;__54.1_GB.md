---
title: "Does ubuntu &quot;weigh&quot;  54.1 GB ?"
date: 2009-03-01
forum: General Help
---

### Post by emshains on 2009-03-01
I've been cleaning my hdd the other day, when I noticed that /home is just 79.4 gb big, but I have just about 27.6 gigs free. This is odd because I have a 160 gig hdd. Is this normal, or there are some caches I could clean ?

---

### Post by woosey on 2009-03-01
Hi,

What happens if you run -

df -h

and 

fdisk -l

Copy the responses into this thread so we can take a look :)

---

### Post by emshains on 2009-03-01
Well, the df -h dropped out this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             150G  115G   28G  81% /
varrun                379M  244K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   56K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   39M  340M  11% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      150G  115G   28G  81% /home/emils/.gvfs

```

But fdisk didn't make any output, just dropped me back to the shell.

---

### Post by woosey on 2009-03-01
Hi,

that looks fine, your showing 150Gb total storage which is about right for a 160gb drive.

If you want to know where the extra space is being used you could try -
```

cd /
du -sh * | grep G | sort -n

```
This will take a little while to run ;) But will give you a summary of the folders in size order.

---

### Post by emshains on 2009-03-01
> **woosey said:**
> Hi,

that looks fine, your showing 150Gb total storage which is about right for a 160gb drive.

If you want to know where the extra space is being used you could try -
```

cd /
du -sh * | grep G | sort -n

```
This will take a little while to run ;) But will give you a summary of the folders in size order.

Thanks  a bunch ! :guitar:

---

### Post by woosey on 2009-03-01
> **emshains said:**
> Thanks  a bunch ! :guitar:

No Problems, if your using X i'm sure you can find out quicker through explorer, however I'm used to having headless servers, so used to the console way round ;)

---

### Post by abhilashm86 on 2009-03-01
ha ha i was shocked to see ubuntu's size:) lol hey you can clarify like this,
if you mount all removable media (hard disks), obviously ubuntu size increases, maybe if you install all in synaptic package, your ubuntu will be of this size:)

---

### Post by Slim Odds on 2009-03-01
It does seem that people are getting a little confused about disk space usage lately.

Really, the "Ubuntu footprint" is really in /usr (/boot is really small).

I have a system with quite a few things installed and my /usr is at about 3.9G

---

### Post by kelvin spratt on 2009-03-01
just check the size of your home folder then look what you have saved in that folder you will then realise how much you have saved. I personally don't save things in my home folder.

---

### Post by emshains on 2009-03-01
Well, I personally haven't done too much packaging, I have installed the ubuntu studio packages and some games, but I don't think that it would all take about 50 gigs. 

Well, ok, let's make it system "weight", but, really, is there like a .deb file cache I haven't been informed about ?

---

### Post by perlluver on 2009-03-01
If you run this command in a terminal ```
sudo apt-get autoclean
``` that will get rid of all the .debs that have been stored up over time of updating.

---

### Post by emshains on 2009-03-01
Well, that deleted one wine .deb, which was 8 mb big. Well, what other space-fillers do you know ?

---

### Post by kidux on 2009-03-01
> **kelvin spratt said:**
> just check the size of your home folder then look what you have saved in that folder you will then realise how much you have saved. I personally don't save things in my home folder.
Where do you save things then? I have /home on a separate partition, with a download directory in it that everything gets saved to.

---

### Post by emshains on 2009-03-01
I save everything in /home/user/folder/. But I already know how much does /home/user "weigh"- 71gb. 
P.S. Hey, could you please give me the wright word that is supposed to be in the "weigh's" place?

---

### Post by jocko on 2009-03-01
> **emshains said:**
> I save everything in /home/user/folder/. But I already know how much does /home/user "weigh"- 71gb. 
P.S. Hey, could you please give me the wright word that is supposed to be in the "weigh's" place?
size?

---

### Post by Zyphrexi on 2009-03-01
i don't know if this is installed by default, but the gnome-utils package contains a disk usage analyzer (baobab) that is nice for checking out disk-usage.

also 'disk-usage' is probably a better descriptor.

---

### Post by Slim Odds on 2009-03-01
> **emshains said:**
> Well, that deleted one wine .deb, which was 8 gb big.

1) What is a "wine .deb"?
2) 8G is **way bigger** than any .deb I've ever seen.
3) I'll bet it was something else....

---

### Post by emshains on 2009-03-01
K, it was 8 mb, not 8 gb, sorry. Emm, it was an installer for wine. And the size of /home/user/ is about 70 gigs, I have 27 gigs of free space, and I have a 160 gb hdd. So where are my 63 gigs ?

---

### Post by Zimmer on 2009-03-01
have you tried the disk usage analyzer, BAOBAB, included in the Gnome Utilities...?

Also, see how much you are using up in your .thumbnails cache....

---

### Post by kelvin spratt on 2009-03-01
Kidux 
You can save on any partition you want to ie downloads sdb1 photos sdb2 music sdc4 etc etc. you don't need to use the home folder for storage my home folder is 15gb and uses 25% its only used for saving user settings.
back to this problem something is very amiss to build up vast amounts of data. I would try using partmagic live cd and use check and repair disc just in case there is a admin fault on the partition then right click on every folder to check the size,  thumbnails can take up a lot of room but that can be emptied.

---

### Post by mulligan.can on 2009-03-01
cd /
sudo du -hc --max-depth=1

That will give you the size of the all the "folders" under /, from there you should be able to work out where all your used space is hiding.

Post it here or work it out yourself.

EDIT: I run it as "sudo" so that you will get the size of /root and any files that you don't have permission for on the off chance that that is where the data is hiding.

---

### Post by kidux on 2009-03-01
> **kelvin spratt said:**
> Kidux 
You can save on any partition you want to ie downloads sdb1 photos sdb2 music sdc4 etc etc. you don't need to use the home folder for storage my home folder is 15gb and uses 25% its only used for saving user settings.
back to this problem something is very amiss to build up vast amounts of data. I would try using partmagic live cd and use check and repair disc just in case there is a admin fault on the partition then right click on every folder to check the size,  thumbnails can take up a lot of room but that can be emptied.
I get that, I just never thought about making it something other than /home/user, except on my server which has a separate 1TB media drive.

---

### Post by emshains on 2009-07-03
Oh my god, why is my /usr/ size 36 gigs ?

I ran this command to check it out: 
```
emils@power-granny:/$ sudo du -sh * | grep G | sort -n
[sudo] password for emils: 
du: cannot access `home/emils/.gvfs': Permission denied
du: cannot access `proc/21521/task/21521/fd/4': No such file or directory
du: cannot access `proc/21521/task/21521/fdinfo/4': No such file or directory
du: cannot access `proc/21521/fd/4': No such file or directory
du: cannot access `proc/21521/fdinfo/4': No such file or directory
1,1G	lib
1,5G	var
36G	usr
99G	home

```

---

### Post by darthmob on 2009-07-03
[baobab]("http://www.marzocca.net/linux/baobab/") is a great program to find out what hogs your hard disk space! it should already be installed or you can get it via synaptic.

---

