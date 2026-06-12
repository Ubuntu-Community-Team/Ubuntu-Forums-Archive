---
title: "USB stick Read-only file system on Dell Mini 9 laptop"
date: 2009-02-18
forum: General Help
---

### Post by asmaia on 2009-02-18
I admit it, I don't understand Ubuntu at all, and I am very dependent on Windows. However, I recieved my first laptop from my parents for Christmas and have tried the best I can to learn what all this gibberish is when you have to type commands in to get anything to work at all. But even Googling answers about this has me still stuck.

I am running Ubuntu 8.04 - the Hardy Heron, and I have a 4GB USB memory stick from Micro Center. It has no lock on it to protect files, so I can't just push something on it to make it writeable. When I first got it, Ubuntu wouldn't recognize it, so I handed it to a friend with a Mac and he formatted it. Not quite sure what he did, but... it worked.

Now, I go between a Windows PC and my Ubuntu laptop just about every day. This tiny little laptop barely has any space at all, and this memory stick is my lifeline. But according to all the searches I've made, I shouldn't have just been pulling the stick out every time I'm done with it, I should 'unmount' it (shouldn't that be eject?), and I've now corrupted it. Seems like the only answer is to format it. Also, it has never ever let me write files to it from Windows, and only works as something to remove files from my laptop, going Ubuntu -> Windows, but not Windows -> Ubuntu.

Is this true? Can I save the stuff on it and not have to constantly format it? How do I format it myself? Can I write both ways? Also, the screen on the Dell Mini 9 is tiny, and I am at the highest resolution allowed, but when I click on the properties of the USB drive, it won't show the whole window and the 'okay' button (or whatever it is supposed to say, because I can't see it), and it won't let me resize it either.

I feel completely lost how to use this.

---

### Post by ajgreeny on 2009-02-18
You may need to do nothing more than use windows again and go through the "Remove safely" procedure in that OS to get it mounting in ubuntu again.  This is a feature of drives formatted to ntfs that are removed incorrectly from windows, where an ntfs filesystem puts a lock on the flash drive filesystem.

However, lets find out how it is formatted first.  Attach the flash drive then open a terminal and enter sudo fdisk -l and report back with the output from that command.  OK, I know it's command line, which you don't seem to like, but it's so much easier than using any gui for this simple information.

---

### Post by asmaia on 2009-02-18
Er... my friend just fixed it for me. He had me type "sudo fsck.msdos -a /dev/sdb1" and I lost some files, but it fixed it. Thank you though!

---

