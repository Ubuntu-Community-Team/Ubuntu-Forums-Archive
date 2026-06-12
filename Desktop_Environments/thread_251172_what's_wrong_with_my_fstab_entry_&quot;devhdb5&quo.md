---
title: "what's wrong with my fstab entry &quot;/dev/hdb5&quot;?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by ke3pup on 2006-09-05
hi guys

i have a partitions on my system in NTFS , i want to have access to it from Linux and let it be automatically mounted on Boot up, i looked in the “how to edit fstab" article to get it working but unfortunately i didn't manage to, here's what i put in fstab to get it working:

/dev/hdb5  /media/hdb5  ntfs   defaults,user,nls=utf8,umask=007,gid=46  0 1
i also tried:
/dev/hdb5       /media/hdb5     ntfs    auto,user,exec, 0       1

When i go in System >> Administration >> Disks , it shows that "access path: /media/hdb5". But if i click "Browse" none of the files in that partition are displayed and only an empty folder titled "hdb5" is displayed! it doesn't get mounted on boot up either....

can anyone tell me what i did wrong? thank you

P.S. i have another NTFS partiton in fstab which was added automaticlly which is:

/dev/hda1    media/hda1    ntfs   defaults,nls=utf8,umask=007,gid=46 0   1

my /dev/hdb5 is close to what's there so why doesn't it work?

---

### Post by orb9220 on 2006-09-05
/dev/hda1 media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
Should be:
/dev/hda1 [COLOR="Red"]/[/COLOR]media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

---

### Post by em3raldxiii on 2006-09-05
I am thinking you may also want to change the umask=007 to something with greater permissions, though I am hesitant to suggest 777.  Others here can probably recommend alternatives.

---

### Post by ke3pup on 2006-09-05
> **orb9220 said:**
> /dev/hda1 media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
Should be:
/dev/hda1 [COLOR="Red"]/[/COLOR]media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
sorry that was my Typo and fstab does have / before media, but the entry in question is NOT /dev/hda1, that one is working perfectly fine, the one that isn't working is :
/dev/hdb5       /media/hdb5     ntfs   defaults,user,nls=utf8,umask=007,gid=46 0       1

like i mentioned i also tried changing it to :

/dev/hdb5       /media/hdb5     ntfs    auto,user,exec, 0       1

but that didn't help either, can anyone help? thanx

---

### Post by orb9220 on 2006-09-05
Here is mine:

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

The second zero use to be a 2 which is disk checking. Changing it to a zero turns off that fearure.

---

### Post by BLTicklemonster on 2006-09-05
Couldn't find /media/hdb1 try again.

I sure would like access to my ntfs drive...

:)

---

### Post by bernied on 2006-09-05
Does the mountpoint (that's the directory in your filesystem that you want the NTFS partition to reside) exist?
When you made that fstab entry, did you also do the following?:
sudo mkdir /media/hdb5
(mkdir is make directory)

If in doubt, try
mount | grep /dev/hdb5
Is there anything there? The mount command on it's own (try it) gives you a list of all mounted filesystems, the grep command searches for the entry that you care about.

If you find an entry for /dev/hdb5 then the partition is mounted and the problem is with accessing the filesystem.

If there is not an entry for /dev/hdb5, try 
cd /media
ls

Is hdb5 there?
If hdb5 is there, then the mountpoint exists and the problem is with the mount command. This would suggest that this NTFS filesystem is somehow different from the one on /dev/hda1 - are the two filesystems from two different operating systems?

If hdb5 is not there, then this is definitely a problem, you need to have a place to mount the filesystem, try:
sudo mkdir /media/hdb5
sudo mount /dev/hdb5

Does that fix the problem?

If not, please post the results of:
mount
and
fdisk -l
and
cat /etc/fstab

Also post any errors you got when trying the above

You might also want to try this:
sudo mount /dev/hdb5 
cat /var/log/messages

So this will try to mount the filesystem, then cat will print out the contents of that log file, and the last part of it should contain information about why you can't mount the partition.

As far as I know, NTFS support is still not rock solid in linux, and you are taking (unnecessary) risks by mounting these filesystems - especially if they contain all the system files for another operating system. Would you not be better off creating a shared area that you have well supported read/write access to using a different filesystem? I recommend FAT32 - it works well in both linux and windows.

---

### Post by BLTicklemonster on 2006-09-05
Wow, cool thanks. I do know that on my now-clicking hard drive, the mount point was totally different, like /bin/something-wierd.something or other, but gee, that's innaccesible now:).

I'll try all that tonight and see what happens.

Thank you for a detailed reply. Stuff like that really helps us noobs immeasurably!

---

### Post by BLTicklemonster on 2006-09-05
in the middle of all this, I lost sudo. Took me all evening to fix, but it's back and I can now access that drive. 

BUT, the partion on the drive I'm using now also has windows on it, ntfs, and it doesn't show up at all. It's at hda5. I have it showing now theoretically, using everything you show up there, but it neither shows up in system>administration>disks, nor in places, computer. BTW, the first drive can be accessed via system>admin>disks, but not through places>computer. I wonder why?


Still at it though. thanks for you help!

---

