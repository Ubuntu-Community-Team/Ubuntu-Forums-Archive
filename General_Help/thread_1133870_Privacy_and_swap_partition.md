---
title: "Privacy and swap partition"
date: 2009-04-23
forum: General Help
---

### Post by GL_NORWAY on 2009-04-23
A possible scenario: you're having Linux on a laptop and is working on some really sensitive data e.g. regarding a top secret corporate project. You have encrypted the sensitive data to protect your business, but each time you decrypt the file or partition to work with the data, Linux uses the swap partition for temporary memory -- so all that sensitive data is temporary stored on the swap partition uncrypted. Then the laptop gets stolen, maybe by a mean rival or someone who wants your critical information very bad. Couldn't they then just scan the swap partition and/or recover any deleted data with recovery software to gain access to the top secret data?

---

### Post by dabl on 2009-04-23
Don't use a swap partition, use a temporary swap file that is built at boot time.  End of risk!  :guitar:

---

### Post by juancarlospaco on 2009-04-23
But Swap are completly Erased at shutdown/boot time.
And usually the system dont use Swap for mentioned tasks, just uses Swap if there isn't more ram avaliable.

---

### Post by Detonate on 2009-04-23
The program "secure-delete" has a feature to wipe the swap drive.  It's in the repositories.

Once installed you can run the feature which is called sswap from the command line.

```
sudo sswap /dev/the device containing your swap file
```

See:

man sswap for options.

---

### Post by fargle on 2009-04-23
You also could consider what I do, which is have your swap encrypted with a random key every time the system comes up - swap doesn't need to exist across reboots.

The only downside is you can't hibernate to the swap area.

[[COLOR="RoyalBlue"]This link[/COLOR]]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu") is for 8.04 but still works as of Intrepid at least, and I don't see any reason it wouldn't work on Jaunty.

---

### Post by GL_NORWAY on 2009-04-23
> **juancarlospaco said:**
> But Swap are completly Erased at shutdown/boot time.
And usually the system dont use Swap for mentioned tasks, just uses Swap if there isn't more ram avaliable.

I don't know how it's like with Linux and Ext3, but when a file or a partition is deleted in Windows FAT32 or NTFS, the data is still on the disc and can be recovered easilly with recovery software. When you delete a file in Windows, the table of content gets updated, but the data is still on the HD. That's the issue with the scenario in the OP.

---

### Post by Detonate on 2009-04-23
From what I have read on this, when a file is deleted (actually deleted, not just moved to trash) in ext3, the space the file occupied is overwritten.  But swap files may be different.  I am required to use a secure delete program on computeres that contain personal data for a tax preperation agency.  I am the only person who uses linux to transfer and store these files, so I use secure-delete to be safe.  I use sswap to do this on the swap file.

[http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

---

### Post by GL_NORWAY on 2009-04-23
> **Detonate said:**
> **From what I have read on this, when a file is deleted (actually deleted, not just moved to trash) in ext3, the space the file occupied is overwritten.**  But swap files may be different.  I am required to use a secure delete program on computeres that contain personal data for a tax preperation agency.  I am the only person who uses linux to transfer and store these files, so I use secure-delete to be safe.  I use sswap to do this on the swap file.

[http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

If this is true, then Linux is a really safe and private OS to use compared to Windows and NTFS! Can anyone verify that Ext3 overwrites the deleted space on the HD?

Thanks for the advices, I'll be checking these tools out! :)

---

### Post by ubu-for on 2009-04-23
> **GL_NORWAY said:**
> Can anyone verify that Ext3 overwrites the deleted space on the HD?

Try Photorec, one of two Testdisk programs, and you will find some really old files deleted long time ago, if they aren't already overwritten.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

[http://ubuntuforums.org/showthread.php?t=1132299](http://ubuntuforums.org/showthread.php?t=1132299)

---

### Post by Detonate on 2009-04-23
I was quoting the link I posted on that, but a google search seems to verify it.  Here's a quote from another site.

[I]Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.[/I]

---

