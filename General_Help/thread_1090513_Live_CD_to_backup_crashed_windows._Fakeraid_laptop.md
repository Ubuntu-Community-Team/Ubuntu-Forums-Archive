---
title: "Live CD to backup crashed windows. Fakeraid laptop."
date: 2009-03-08
forum: General Help
---

### Post by jordanthegreat on 2009-03-08
Hey all.

Complete linux newb here. I have with me a windows laptop that will not boot. I am trying to use a Ubuntu Live CD to backup some important files before wiping it. I was following the instructions on [this page](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)  when I encountered a problem running this *mount -t ntfs-3g /dev/sda1 /media/disk -o force*. Basically I am trying to force mount the hard drive so I can access the files. Turns out this laptop has 2 hard drives in raid 0 (from what I have read in other places im guessing it is fakeraid). Here is the exact message I get when I try to run the code I mentioned.

> root@ubuntu:~# mount -t ntfs-3g /dev/sda1 /media/disk -o force
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


Being the newb that I am, without good instructions on where to go from here, I am totally lost. Any help you guys can provide me is much appreciated.

Cheers,
Jordan

---

### Post by Slim Odds on 2009-03-08
I'm highly doubtful that you have fakeRaid on your laptop.

The error message is saying that windows did not shut the drive down cleanly (which always happens when windows crashes).

You may need to install ntfsprogs and run ntfsfix on the drive before you can mount it.

---

### Post by jordanthegreat on 2009-03-08
I know for sure that I have 2 hard drives in raid0 though. Wether it is fakeraid or not, that I know nothing about. But ok, ill try what you suggested and report back. Thanks for your help.

---

### Post by jordanthegreat on 2009-03-08
ok, like i said, im a major newb here. so how exactly do i install ntfsprogs? and i tried to run ntfsfix and this is the error i got:

> root@ubuntu:~# ntfsfix /dev/sda1
Mounting volume... Error opening partition device: Device or resource busy.
Failed to startup volume: Device or resource busy.
FAILED
Attempting to correct errors... Error opening partition device: Device or resource busy.
FAILED
Failed to startup volume: Device or resource busy.
Volume is corrupt. You should run chkdsk.
root@ubuntu:~# ntfsprogs
bash: ntfsprogs: command not found

---

### Post by Slim Odds on 2009-03-08
> **jordanthegreat said:**
> ok, like i said, im a major newb here. so how exactly do i install ntfsprogs? and i tried to run ntfsfix and this is the error i got:

Commands that work directly on disk drives require sudo.

```
sudo ntfsfix /dev/sda1
```

---

### Post by Dustin2128 on 2009-03-08
out of curiosity, why won't your windows os boot?

---

### Post by jordanthegreat on 2009-03-08
When I try to boot it, all I get is a black screen with a message saying "Missing operating system"

I am actually fixing it for a friend. He said one night it was working fine, then the next day he tried to boot it but as windows was about to come up it would reboot automatically and just keep looping like that. After trying a few times to get it to boot normally, it just went to "Missing operating system".

---

### Post by jordanthegreat on 2009-03-08
Ok, here is an update. I figured out the raid volume label is simply "RAID0" so I thought maybe entering this could work:

> mount -l RAID0 media/disk -o force

That gives me the following error:

> mount: special device RAID0 does not exist

Is what I am trying here even within the ballpark of what I should be doing? Please advise.

Cheers,
Jordan

---

### Post by Slim Odds on 2009-03-08
Try: man mount

---

