---
title: "Mounting an External Hard Drive"
date: 2009-01-14
forum: General Help
---

### Post by Pintzize on 2009-01-14
I have Ubuntu 8.40 and a Cavalry 500gb Hard drive. I have been using this for a while and all was working well but today I booted up my computer and when I turned on my computer it said "Can't mount Volume" For Details it says this:

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

I don't have a windows partition so I have no idea why it's talking about windows. I've tried mount /dev/sdc1 /media/Serenity but it just says that again.

---

### Post by dcstar on 2009-01-14
> **Pintzize said:**
> I have Ubuntu 8.40 and a Cavalry 500gb Hard drive. I have been using this for a while and all was working well but today I booted up my computer and when I turned on my computer it said "Can't mount Volume" For Details it says this:

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

I don't have a windows partition so I have no idea why it's talking about windows. I've tried mount /dev/sdc1 /media/Serenity but it just says that again.

Do a fsck on it - but it may be corrupted.

---

### Post by mc4man on 2009-01-14
If it is a NTFS volume then there's ntfsprogs. (in synaptic

The ntfsfix utility can do some minor repairs.

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

There doesn't appear to be a ntfsck availabe yet, though there is an alternative

---

### Post by marc raes on 2009-04-01
I get the same message for my maxtor basics 500gb external drive.
I have a dual boot jaunty/vista and it mounts in vista.
Is this a jaunty problem?
This is really silly. Bought the thing to store iso files and I can't use it!
Has anybody found a solution?

---

### Post by marc raes on 2009-04-29
> **Pintzize said:**
> I have Ubuntu 8.40 and a Cavalry 500gb Hard drive. I have been using this for a while and all was working well but today I booted up my computer and when I turned on my computer it said "Can't mount Volume" For Details it says this:

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

I don't have a windows partition so I have no idea why it's talking about windows. I've tried mount /dev/sdc1 /media/Serenity but it just says that again.

Is, what you talk about, an external hard-disk with usb-plug?
I managed to fix this maxtor-external-disk I use.
I couldn't mount it anymore and got the same message as you.

So I plugged it in, ignored the message and opened the graphical partition-manager. It found the disk. So I right-clicked on it and got the choice to reformat it to different kinds of file-type. (ntfs was not among the choices). So I opted for ext3, as Fat32 can't handle files larger than 4Gb.
I clicked on "apply changes". And it neatly formatted it as ext3. After that I could mount it en read and write on it.

Because it has to be used on window-computers also, I ended up reformatting the disk to ntfs in vista.

As you don't use windows you could settle for ext3. Maybe ntfs is sustained for your disk or ask a friend to format it for you in windows.

The big drawback: formatting removes all the files, stored on your disk already!
So I'd suggest: contact a windows-friend. Windows will probably mount the blackguard-disk. And you could then copy your files to another device.

---

### Post by green0eggs on 2009-07-25
I had the same error message pop up all of a sudden but managed to **save the world** (actually, just the data on the partition) with [**ntfsfix**]("http://man.linux-ntfs.org/ntfsfix.8.html") as suggested by mc4man (thanks).

I already had the ntfsprogs package, ran:

```
sudo ntfsfix /dev/sdb2
```

...where sdb2 was the partition table entry for the buggy disk.

This is the output I got:
```

Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 0...OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb2 was processed successfully.

```

It'd be a shame for anyone reading this to just re-format a la marc raes (above). Some instances of the error can clearly be er... fixed.

---

### Post by atngplusultra on 2009-08-09
Is it normal for the emptying of the journal to take quite some time? My drive seems to have been working at this for a while now...

edit: in fact, it's been nearly twelve hours and my terminal is stalled on the step:

```

Going to empty the journal ($LogFile)... OK

```

is there any reason for this?/what should i do?

---

