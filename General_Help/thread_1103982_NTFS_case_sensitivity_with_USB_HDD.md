---
title: "NTFS case sensitivity with USB HDD"
date: 2009-03-23
forum: General Help
---

### Post by thevoicesdoneit on 2009-03-23
Hi,

I have a problem with mounting an NTFS-formatted USB HDD.

I know that NTFS is case sensitive as is ext3 etc but I appear to get a problem when I rsync files to the external USB HDD/rename items on it.

I've copied some files to the USB drive using a directory comparison tool called "Beyond Compare" and then later run an automated "rsync" backup that effectively automatically did what I did manually in Beyond Compare. Afterwards, I have duplicate files in the folders that I backed up; each duplicate is represented by one copy of it having an "all" lowercase name and the other as all uppercase.

There is another problem in that if I have a folder called, for example, "cd1" and I try to rename it to "CD1" then nautilus complains that the directory already exists(!) 

So, I'm not sure that the problem is brought on by Beyond Compare but that there is a more fundamental problem.

I've read a few items about there being some issues/bugs in this regard but is there a way to get Ubuntu to mount *any* USB HDD that I add, that happens to be formatted for NTFS, so that it treats the filenames and directories in the same way as if I mounted it from a windows box?

Thanks in advance,
V

---

### Post by thevoicesdoneit on 2009-03-23
*bump*

---

### Post by Proteusiq on 2009-03-23
[http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+ntfs](http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+ntfs)

This one did work for me! Hope it will do for you!

---

### Post by thevoicesdoneit on 2009-03-23
I'm not sure how that helps. I'm not having trouble mounting the HDD - I'm having trouble with the case sensitivity of it when I've mounted it.

---

### Post by thevoicesdoneit on 2009-03-25
Is there no solution for this then?

---

### Post by 3Miro on 2009-03-25
> **thevoicesdoneit said:**
> Is there no solution for this then?

This might be rsync/Beyond Compare issue. I have been accessing NTFS partitions from within Ubuntu for years and I don't remember having lower/upper case issues. The case was preserved for me.

---

### Post by coffeecat on 2009-03-25
I have absolutely no experience of Beyond Compare, but I agree that this could be a BC issue, because:

> **thevoicesdoneit said:**
> There is another problem in that if I have a folder called, for example, "cd1" and I try to rename it to "CD1" then nautilus complains that the directory already exists(!)

I've set up the internal sdb on this machine with one partition, formatted NTFS. I've just tried creating (in Ubuntu 8.10/gnome) a folder called "cd1". Then I right-clicked on it and renamed it to "CD1". Not a murmur from Nautilus; folder renamed OK. And like the previous poster, I've not experienced any case issues with my external NTFS drives.

---

### Post by thevoicesdoneit on 2009-03-25
OK, thanks for that information.

After looking at this again, I tried creating some folders on an NTFS drive and it works as you say..I can have a combination of 

CD1
cd1
cD1
Cd1 

without any problems.

After having a re-think, it could be that the original files live on a FAT32 partition which is case sensitive. If I try to create a folder called 'CD1' on my FAT32 partition, it renames it to 'cd1' which surprises me in a way because I thought that FAT32 filenames were generally all upper case. 

If I then try to rename my 'cd1' folder to 'CD1', nautilus says that the folder already exists, which makes some kind of sense.

So, I then created a VFAT test folder with some directories in it:
CD1 (which became cd1)
CD2 (which became cd2)
NIN (which became nin)

If I rsync this test folder to a NTFS partition, the filenames all get copied as lower case.

If I delete the rsync'd dirs then sync with "beyond compare", the folders get recreated in lower case(!)

I'm none the wiser as to what went wrong before now(!) although I think I should migrate all my partitions over to NTFS (or ext3) to get around folders being renamed to lower case.

Is there a good reason NOT to use NTFS under Ubuntu these days? 
Is it possible to format partitions for NTFS under Ubuntu?

Thanks in advance,
V

---

### Post by kanikilu on 2009-03-25
I've noticed this same behavior on a FAT32 formatted drive. It doesn't matter if I create the directories via the terminal or nautilus, almost at random, when I check it later, some of the directories will have lowercase names when I know I created them with uppercase. So, it may not necessarily be a problem specific to the software you are using...

---

### Post by thevoicesdoneit on 2009-03-25
Furthermore....

If I look on my FAT32 partition, I see folder names that are a mixture of upper and lower case:

e.g.

"/media/mount/eBooks and Info"

Now, if I create a new folder "EBOOKS" (this is what I type into nautilus), it gets renamed to "ebooks"

If I create one called "eBooKs", it doesn't get renamed.

If FAT32 is case insensitive, why does the FAT32 mount get treated with case sensitivity? That doesn't make sense. For it to be consistent, you'd expect it to rename "eBooKs" to ebooks if it renames "EBOOKS" to 'ebooks', yes? Why the difference????

---

### Post by coffeecat on 2009-03-25
> **thevoicesdoneit said:**
> Is there a good reason NOT to use NTFS under Ubuntu these days?

I can't think of one. So far, I've not had any problems with NTFS partitions/drives, and NTFS has the advantage of supporting files larger than 4GB and of being more robust than FAT32. However, on the subject of robustness, if the journal does get corrupted and the filesystem needs repairing, I don't know whether the Linux NTFS tools are yet up to the job. It's a good idea to keep a Windows installation going, just so that you can do a chkdsk if necessary. It's the only reason I keep Windows going these days anyway. :)

And the advantage for me with NTFS is that it does **not** support Unix permissions. That might seem strange to say, but although I run Ubuntu as my main OS, I like to play with other distros. Ubuntu sets the UID of the first created user as 1000, whereas some of the rpm distros like Mandriva and Fedora set it as 500. With a shared ext3 partition you run into permission problems. With NTFS, there's no problem. As a single user with no other accounts to worry about that's a big plus for me.


> **thevoicesdoneit said:**
> Is it possible to format partitions for NTFS under Ubuntu?

I often use Gparted to create NTFS filesystems. I can't remember whether you have to install ntfsprogs first, but if you find Gparted won't create a NTFS filesystem, just install ntfsprogs and you'll be good to go. You can even label a NTFS partition with one of the utilities that comes with ntfsprogs called, unsurprisingly, ntfslabel.

---

### Post by thevoicesdoneit on 2009-03-25
Thanks for that input.

I have run into permissions problems before, which is mostly why I use FAT32 for a large proportion of my partitions since I want to access them from Windows (which I rarely use anyway). I've not often used NTFS because, until today, I didn't realise that you could format them from Ubuntu.

You do have to install ntfsprogs as well as gparted in order to format to NTFS which I intend to do after I've backed up my FAT32 partitions.

I still think there is a consistency issue in how FAT32 partitions are used and abused, though, since it appears that folders that are "all uppercase" get renamed but mixed case ones do not. I'm sure there is a good reason for it...I just can't think of one ;-)

---

### Post by jocko on 2009-03-25
> **kanikilu said:**
> I've noticed this same behavior on a FAT32 formatted drive. It doesn't matter if I create the directories via the terminal or nautilus, almost at random, when I check it later, some of the directories will have lowercase names when I know I created them with uppercase. So, it may not necessarily be a problem specific to the software you are using...

FAT32 is NOT case sensitive (but it *should* preserve the case of a file name).
Not even Microsoft seems to be sure if NTFS is case sensitive or not. [Here]("http://support.microsoft.com/kb/100625") they claim it is, [here]("http://support.microsoft.com/kb/100108") they claim it both is and is not... I guess the truth is that the actual file system is case sensitive, while most windows and DOS applications are not.
So it's no wonder there are problems using ntfs under linux... not even microsoft's own software can handle their file system properly...

---

### Post by thevoicesdoneit on 2009-03-26
Can anyone say why, when working on a FAT32 partition, Nautlus behaves as follows:

1. Create folder called "ThisFolder" - stays as "ThisFolder"
2. Create folder called "thisfolder" - stays as "thisfolder"
3. Create folder called "THISFOLDER" - changes to "thisfolder"

??

That would seem to be an inconsistency (i.e. bug) to me.

This is an issue....

[https://bugs.launchpad.net/ubuntu/+bug/202394](https://bugs.launchpad.net/ubuntu/+bug/202394)
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/315782](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/315782)

---

### Post by coffeecat on 2009-03-26
> **thevoicesdoneit said:**
> 1. Create folder called "ThisFolder" - stays as "ThisFolder"
2. Create folder called "thisfolder" - stays as "thisfolder"
3. Create folder called "THISFOLDER" - changes to "thisfolder"

Nope. Not here with Ubuntu 8.10 and using Nautilus. On an internal partition and on an external USB drive, both formatted FAT32, "THISFOLDER" stays as "THISFOLDER".

Of course, if I leave the folder named "THISFOLDER" and try to create a second called "ThisFolder" I get a 'name already in use' type error. Which is what you'd expect considering the limitations of VFAT.

---

### Post by thevoicesdoneit on 2009-03-27
Is your internal drive mounted via fstab? Can you post the relevant line, please?

---

### Post by coffeecat on 2009-03-27
> **thevoicesdoneit said:**
> Is your internal drive mounted via fstab? Can you post the relevant line, please?

No, I'd automounted it from the desktop. I'm in Jaunty Beta atm (Looking good :wink: ), but a quick experiment shows it's preserving 'THISFOLDER' as all caps just as in Intrepid. I've had to automount here as well, so here is the relevant /etc/mtab line:

```
/dev/sda3 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```That should work in fstab. Just make sure your uid is 1000, or change accordingly.

---

### Post by thevoicesdoneit on 2009-03-27
I think the difference is the 'shortname=mixed' option. I didn't have this included in my mount but I've seen it mentioned in one of the "bug" reports for vfat.

I've reformatted all my old VFAT partitions (I couldn't think of a good reason why they shouldn't be since NTFS is r/w supported in Ubuntu) to NTFS now so maybe the issue is irrelevent for me now.

Thanks for the support

---

