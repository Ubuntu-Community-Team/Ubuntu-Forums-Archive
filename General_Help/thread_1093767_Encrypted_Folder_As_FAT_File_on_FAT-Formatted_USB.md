---
title: "Encrypted Folder As FAT File on FAT-Formatted USB"
date: 2009-03-11
forum: General Help
---

### Post by SuperMike on 2009-03-11
I have a FAT-formatted USB thumb drive that's about 4GB. I'm running Ubuntu 8.04.2 on my laptop. Is there a way to put a file on my thumb drive so that I can mount it as an encrypted folder on my laptop?

---

### Post by SuperMike on 2009-03-12
Nobody got a hyperlink to suggest?

---

### Post by unutbu on 2009-03-12
See "How can I use TrueCrypt on a USB flash drive?"
[http://www.truecrypt.org/faq.php](http://www.truecrypt.org/faq.php)

PS. I've been reading your blog/thread:
[http://ubuntuforums.org/showthread.php?t=645229](http://ubuntuforums.org/showthread.php?t=645229)
very interesting stuff; thanks!

---

### Post by SuperMike on 2009-03-13
> **unutbu said:**
> See "How can I use TrueCrypt on a USB flash drive?"
[http://www.truecrypt.org/faq.php](http://www.truecrypt.org/faq.php)

PS. I've been reading your blog/thread:
[http://ubuntuforums.org/showthread.php?t=645229](http://ubuntuforums.org/showthread.php?t=645229)
very interesting stuff; thanks!

Thanks. I have trouble sleeping most nights, and suffer from ADD occasionally, and live in the middle of nowhere with no technical release. so the blog/thread has been very satisfying.

Thanks for the link. I couldn't figure out how to get it going with Linux, but I have good news. I found I can install something super easy and get exactly what I need. It comes with Ubuntu 8.04 and it's called cryptkeeper.

You just install it like so:

$ sudo apt-get update
$ sudo apt-get install cryptkeeper

Now mount your USB thumb drive and it doesn't matter whether it's EXT3, EXT4, ReiserFS, NTFS, FAT, or FAT32 -- it's all the same with this thing.

And then to launch cryptkeeper, I do:

$ sudo cryptkeeper &

Now look in your notification area and there's a new icon of some keys. Click the keys and choose New Encrypted Folder. Select your thumb drive and type in a new folder name like ".settings". Now, what's confusing is that in the lowerhand corner is a button called Forward. Click that.

Now enter the password and confirm.

And poof, you get a new window with your mounted, encrypted volume. Copy your critical private folders to it. (Like pirated music and movies, company proprietary data, invoices, etc.)

To unmount, click the keys icon in your systray and uncheck the folder you just created. Now, if you had any terminal windows with a 'cd' into that thumb drive directory, then you need to 'cd' out, such as 'cd /', or close the terminal windows. And if you have any folders open to this location, close them. Last, go to your GNOME desktop and rightclick the volume and choose Unmount Volume. After 2 seconds and the lights stop flashing, remove the drive.

Now if you lose your thumb drive, you can rest assured that the folder you created is [Blowfish encrypted]("http://en.wikipedia.org/wiki/Blowfish_(cipher)") with your password. The finder of your drive can open the folder and see files, but everything is encrypted -- folder names, file names, and data.

To remount, stick your thumb drive in, and if cryptkeeper isn't open, do:

$ sudo cryptkeeper &

(You might also be able to use 'gksudo /usr/bin/cryptkeeper' from your sessions control panel in GNOME.)

Now click the keys and check the checkbox for the volume. A folder will appear before you with unencrypted folders.

---

