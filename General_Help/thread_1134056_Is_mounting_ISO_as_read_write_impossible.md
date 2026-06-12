---
title: "Is mounting ISO as read write impossible?"
date: 2009-04-23
forum: General Help
---

### Post by Saibot Sivad on 2009-04-23
This is a more technical question, a fundamental if you will:

Situation:
I have an ISO and I need to change a small file inside it. When I mount it using GUI commands ("Open with 'Archive Manager'" and "Open with 'Archive Mounter'") it is read-only. When I mount it with command line, even specifying read-write and using sudo, like so:
sudo mount -o rw,loop disk.iso /media/disk
It silently mounts it, so I assume everything is good. Except when I go to modify files, it says it is a read-only file system.

Questions:
1) Is it possible to mount an ISO to be read-write?
2) If it is not possible, isn't that poor user interface? Shouldn't it tell you something like "You can't do that" instead of running like normal?
3) Also, if it's not possible, is there any other solution than "mount, copy, modify, mkisofs"?

More:
I read around online, found a lot of posts with this same topic, and all of them had a "solution" of copying the ISO content to the hard drive, modifying it, and making a new ISO. This is what I eventually did, so you don't need to suggest it. However, may I posit that it is *not* a good solution in all cases? E.g., I have a 6GB ISO on the drive, mount it (that makes 12GB), modify, make new ISO (thats 18GB). I mean, maybe that's not the norm, or maybe I made an ISO when I should have made an IMG? Am I missing something?

Summary:
Can somebody tell me, from a technical point of view, if I can or why I can't mount an ISO as read-write?

---

### Post by dabl on 2009-04-23
Well, I don't know if it is "technical" enough, but I think the simple answer is - ISO image files are compliant to a standard, and that standard does not include a "user writable" feature.

You can't write to a TIFF file, right?  You can only change it and then re-save the entire image.  ISO 9660 is a special _image_ format, analogous (if not similar) to TIFF.

---

### Post by kanikilu on 2009-04-23
From Wikipedia:> ISO 9660 is by design a read-only, pre-mastered, file system. This means that all the data has to be written in one go to the medium. Once written, there is no provision for altering the stored content. **Therefore ISO 9660 is not suitable to be used on random-writable media, such as Hard Disks**.

---

### Post by LateNiteTV on 2009-04-23
[http://www.linuxquestions.org/questions/linux-software-2/editing-iso-images-mounting-read-write-271314/](http://www.linuxquestions.org/questions/linux-software-2/editing-iso-images-mounting-read-write-271314/)

---

### Post by Saibot Sivad on 2009-04-30
Thank you all for your replies, I think I may understand better. It seems that the ISO 9660 format just does not allow for the possibility of read-write. So in the case of me having an ISO file on my drive, I would have to mount>copy>edit>mkisofs to do even the smallest bit of editing.

@LateNiteTV: Thanks for your response, but I had actually read that very post already, along with about twenty others just like it. I was not looking for a how, more a fundamental "why not".

@dabl: I think that is pretty good reasoning, although in the case of modifying an ISO *file* on the drive it makes it difficult and time consuming. I suppose the payoff is better, thus it's use.

Anyway, it seems that there are two ways for me to go about it:

1) Don't copy the disk or drive as an ISO originally, instead I could use something like an IMG file. This method is useful for future planning, although ISO files would still have their uses.

2) If I absolutely positively have to modify an ISO, the way to do it is, in general, as follows:

First, mount the ISO as a cdrom:
mkdir /mnt/iso
mount -o loop /path/to/iso /mnt/iso

Then, copy everything off the ISO:
mkdir /tmp/iso
cp -a /mnt/iso /tmp/iso

Modify the file(s) that I need modified. Now take those files and make them into a new ISO (from earlier mentioned link):
mkisofs -R -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o /tmp/new.iso /tmp/iso

The "-b" flag makes the disk bootable, using "isolinux/isolinux.bin" as the boot file. The "-no-emul-boot", "-boot-load-size 4", and "-boot-info-table" all are extra settings for making the disk bootable. The "-c isolinux/boot.cat" is a packaging flag. The "-o /tmp/new.iso" is the file it will generate, and the last thing "/tmp/iso" specifies the files to put inside it. The "-R" makes sure the final ISO file is fully compliant.

Anyways, thanks everyone for your thoughts. It seems like modifying a small file on an ISO is made more complex because the ISO protocol is not set up to allow a read-write possibility.

---

