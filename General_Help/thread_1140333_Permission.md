---
title: "Permission"
date: 2009-04-27
forum: General Help
---

### Post by texas.chef94 on 2009-04-27
I have a goodly number of files to move to my data partition and I am wondering if there is a more convenient way
1. I enter into terminal gksudo nautilus which activates the root file browser. So every file I have intention of moving to partition must be conveniently on my desktop to drag and drop, and I assume this is moving the files to my partition
Is this correct so far
On the other if I go to nautilus click on 160 GB media the window that opens denies me without permission. Can I get permission there
I am confused
Is not the disk file browser the conventional access to my data partition
Please advise

Allen

---

### Post by ajgreeny on 2009-04-27
Yes it is, but the mounted data partition must be owned by root at the moment, so you need to change that to your username.  I assume that the partition is mounted in /media in this example, but if not change the detail of the command below to suit your own mount point, and obviously add your own username instead of the actual word "username".  Open a terminal and use the command ```
sudo chown -R username:username /media/mountpoint
```That should do it.

---

### Post by texas.chef94 on 2009-04-27
Thank you so much

---

### Post by texas.chef94 on 2009-04-27
May I ask one other question pertaining to this thread. I thought I had created data as mount point. 
As you can see I tried both
allen@allen-desktop:~$ sudo chown -R allen:allen /data/mountpoint
chown: cannot access `/data/mountpoint': No such file or directory
allen@allen-desktop:~$ sudo chown -R allen:allen /media/mountpoint
chown: cannot access `/media/mountpoint': No such file or directory

 Trust me it is mounted as I can go to nautilus and there the 160GB is located left file tree and clicking on that brings up the window with lost+found folder

what I need I guess is command that will tell me what point is

Please advise

---

### Post by ajgreeny on 2009-04-28
Forgive me, but I hope you actually made a folder called "/data/mountpoint" on your filesystem using ```
sudo mkdir /data/mountpoint
```If not the disk will not actually be mounted, though it will still show in "Places" in the left hand pane of nautilus.  It will not actually open to show the files though, I suspect.

Your problem, you see, is that before you can mount a partition, there must already exist the folder you want to mount it to, whether you mount it automatically at boot from /etc/fstab, or manually with the terminal.  The error message suggests that you do not have the folder already made on your system.

If it is a usb disk partition, it should mount automatically when attached to /media/*mountpoint, *the italics part showing as either "sdx#" or whatever the partition was labelled when it was made.

I hope that all makes sense to you.  If not come back again with more questions, and more info about where the partition is, ie what disk type, etc etc.

---

### Post by texas.chef94 on 2009-04-29
> **ajgreeny said:**
> Forgive me, but I hope you actually made a folder called "/data/mountpoint" on your filesystem using ```
sudo mkdir /data/mountpoint
```If not the disk will not actually be mounted, though it will still show in "Places" in the left hand pane of nautilus.  It will not actually open to show the files though, I suspect.

Your problem, you see, is that before you can mount a partition, there must already exist the folder you want to mount it to, whether you mount it automatically at boot from /etc/fstab, or manually with the terminal.  The error message suggests that you do not have the folder already made on your system.

If it is a usb disk partition, it should mount automatically when attached to /media/*mountpoint, *the italics part showing as either "sdx#" or whatever the partition was labelled when it was made.

I hope that all makes sense to you.  If not come back again with more questions, and more info about where the partition is, ie what disk type, etc etc.

Greeny:
Thank you so much for that last gem of wisdom I sorely needed. You have been most kind.
Seeing you were from UK thought I might inject a bit of English culinary lore. Recognize that uniform?
[http://s577.photobucket.com/albums/ss219/worthamtx/](http://s577.photobucket.com/albums/ss219/worthamtx/)
Allen

---

### Post by ajgreeny on 2009-04-29
I'm glad it made sense.  I wrote it, read it, and then thought "I don't think that is too easy to follow" but was presumably wrong about that.  Anyway, good to hear that it made sense to you after all.  It does take a while to get to grips with Ubuntu and linux in general, but once you've done it everything becomes second nature to you, and it makes Windows XP seem very, very convoluted.  I certainly find it difficult to navigate my way round that file-system now, and linux makes so much more sense to me and is a lot more intuitive, I think.

Enjoy yourself.

---

