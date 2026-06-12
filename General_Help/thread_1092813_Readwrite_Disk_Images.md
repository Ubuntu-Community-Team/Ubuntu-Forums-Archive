---
title: "Read/write Disk Images"
date: 2009-03-10
forum: General Help
---

### Post by Peasantoid on 2009-03-10
So I recently had to go for an extended period without my iPod. Tunez-addicted as I am, I needed to find a way of bringing it along without *actually* bringing it. I copied */dev/sdc2* (my iPod's drive) into a file called *ipod.img* and was able to mount that with the following command:
```
sudo mount -o loop ~/ipod.img /media/ipod
```
But for some reason, I can't write to the mounted filesystem. I'm perfectly capable of writing to the physical iPod when it's mounted, but it doesn't work for the image. I've set the file's permissions to -rwxrwxrwx but that hasn't affected anything.

Any ideas?

[edit] By the way, it gives the error "Read-only file system" whenever I try to modify files.

---

### Post by Neo_The_User on 2009-03-10
write to it using sudo. and take out loop in your mount command.

---

### Post by avtolle on 2009-03-10
This makes sense to me, although I've nothing to which to refer you. An image file is just that; a file that is a bit for bit copy of another file (or group of files, such as an image of the ipod disk). If said image file could be altered by being written to, it would no longer be an image file. Thus, perhaps the better way would not be to make an image file of your ipod's disk, but to rather copy the files contained thereon into a directory (folder) with the correct permissions, and in any event, not give it an img file extension. I don't know whether this makes any sense, but logically, an image file should be read-only and not capable of alteration. JMO.

---

### Post by Peasantoid on 2009-03-10
> **Neo_The_User said:**
> write to it using sudo. and take out loop in your mount command.
Unfortunately, neither of these seems to work. For instance, *sudo touch /media/ipod/test_file* still gives the "read-only filesystem" error. Taking out loop (I assume you mean the following):
```
sudo mount ~/ipod.img /media/ipod
```
...gives this error:
```
mount: /home/peasantoid/ipod.img is not a block device (maybe try `-o loop'?)
```

> **avtolle said:**
> This makes sense to me, although I've nothing to which to refer you. An image file is just that; a file that is a bit for bit copy of another file (or group of files, such as an image of the ipod disk). If said image file could be altered by being written to, it would no longer be an image file. Thus, perhaps the better way would not be to make an image file of your ipod's disk, but to rather copy the files contained thereon into a directory (folder) with the correct permissions, and in any event, not give it an img file extension. I don't know whether this makes any sense, but logically, an image file should be read-only and not capable of alteration. JMO.
Well, my aim was not so much to generate a backup as to keep a non-physical copy of my iPod with me &#8212; a copy to which I can read and write songs and stuff, then restore it back to the device's drive later. I also wanted Rhythmbox to be able to automatically detect it (I'm lazy like that), which is why I tried to use it as a disk. Still, thank you for your input. :)

I have also tried manually using *losetup*, then mounting the loop device. This had the same (i.e. none) effect.

---

