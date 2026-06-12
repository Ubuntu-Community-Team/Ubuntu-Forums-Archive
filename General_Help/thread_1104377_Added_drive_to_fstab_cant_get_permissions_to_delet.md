---
title: "Added drive to fstab cant get permissions to delete folders etc"
date: 2009-03-23
forum: General Help
---

### Post by Fenris_rising on 2009-03-23
Hi all

Well I took the bull by the horns and edited my fstab file by hand rather than use the disk manager app I downloaded to add my 320GB HDD. So far I have 99% success with it, but, I don't have 'permissions' to delete any files or folders within the HDD in question. Here is what I have done following various guides indicated by this forum.

Identified my HDD UUID and TYPE

Ran this code first to set a mount point.

```
mkdir /media/disk
```

Then added the following to my fstab. Now My UUID I understand. media/disk is the mount point. auto could also be ntfs as the HDD is in the ntfs format. After that I haven't a clue and this may be the cause of the problem I am having.

```
UUID=7A3B6D386C9918C4 /media/disk auto rw,umask=0222 0     0
```

this was then followed by the code.

```
sudo mount -a
```

Then the following lines were executed for ownership and permissions setting.

```
sudo chown -R fenris:fenris /media/disk
```
```
sudo chmod -R 755 /media/disk
```

OK all well and good my HDD is mounted at boot and files within that I have set as shared remain shared even after a reboot and I can move files and folders around via the GUI.

However heres the thing I do not have permissions to delete files or folders and I cannot create new folders on the HDD. I can of course do this via terminal but I wish to be able to do it once more via the right click option.

I am pleased I actually got it working as far as it is by hand but I obviously do not understand something here and I am starting to bounce of the walls slightly as I've read myself to death and still can't see what I have done wrong. So..........help me please my sanity is at stake :D

regards

Fenris

---

### Post by drs305 on 2009-03-23
Ownership of ntfs file systems is established at the time of mounting. Thus it won't let you change ownership afterwards. You can solve this by adding your userid to the fstab entry. Since you know this is an ntfs partition, personally I would change "auto" to "ntfs" but it is not necessary.
```

UUID=7A3B6D386C9918C4 /media/disk auto uid=1000,rw,umask=0022 0  0

```

If you don't know your userid (usually 1000 for the first user), run "id" in terminal.

---

### Post by bodhi.zazen on 2009-03-23
Well, ownership and permissions depend on the file system. FAT and NTFS are not the same as ext3 or linux native file systems.

See : 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Fenris_rising on 2009-03-23
Hi all

Thanks for your replys. Between you and a further 'tweak' my end I can now manipulate my files and folders on the HDD. This is the fstab entry I have now. The umask=0222 has been changed to umask=000 which seemed to complete the feature list (I still couldn't create new folders or documents) Thanks to you all for helping me out.

```
UUID=7A3B6D386C9918C4 /media/disk ntfs-3g uid=1000,rw,umask=000 0  0
```

regards

Fenris

---

### Post by jo4hnc on 2009-03-23
bodhi.zazen,

Thanks for the fstab info. I've been trying to change the ownership of a ntfs external drive all day and now I know why it hasn't worked.

John

---

### Post by bodhi.zazen on 2009-03-23
> **jo4hnc said:**
> bodhi.zazen,

Thanks for the fstab info. I've been trying to change the ownership of a ntfs external drive all day and now I know why it hasn't worked.

John

You are most welcome ;)

ownership and permissions on FAT / NTFS are common questions.

---

### Post by jo4hnc on 2009-03-23
Guess they don't call you a guru for nothin'!!

I posted a link to this thread in my posting in case anyone else was having the same problem. 

j

---

### Post by Fenris_rising on 2009-03-24
Guru's one and all :D But even then despite all the reading it takes a little time for things to sink in and make enough sense to be able to action them. How pleased was I this morning when I turned on my PC and all was as it should be :D Very pleased!

regards

Fenris

---

### Post by jo4hnc on 2009-03-24
Not to use a rally bad pun(oh yes it is!!).

Built by association!!

The help on the forum is really priceless.

John

---

