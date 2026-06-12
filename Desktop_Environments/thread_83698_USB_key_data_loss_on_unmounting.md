---
title: "USB key data loss on unmounting"
date: 2005-10-29
forum: Desktop Environments
---

### Post by csaveanu on 2005-10-29
Hi,

I'm a MacOS X and Windows user, recently trying to convert to Linux (Ubuntu). I was very happy with it and impressed by many features (a critical one being that Hibernate worked correctly on my Gericom AMD Wegbine 1400+ laptop without any modifications :D ).  Although I had some adaptability problems, I could find answers to my questions until now by searching with Google on different forums/FAQ. However, I've experienced several times a very annoying problem with my USB key (Creative MuVO V200, 512 Mb) and another key as well:

First, the **file transfer rate** in writing is clearly **superior** to that with Windows (I'm using this USB2 key on a USB1 port on a Gericom laptop). So far so good, but some mp3 files did not transfer correctly; couldn't be read as valid mp3 and I had to re-copy them from the hard disk; so here is my first question - would you expect to have transfer errors with Linux and is there any way to enforce controlling that transferred files are correctly transferred ?

Now, more problematic, when I'm trying to **unmount** the key from the desktop (right-click menu, Unmount) I get an error message saying that /dev/sda couldn't be found but the icon of the key dissapears from the desktop. I assumed it was safe to get out the key from the usb port (anyway no writing/reading was performed at that time). However, none of the files that I thought written on the key previously to unmounting was present on the drive. 

More puzzling, some files written 30 minutes before on the same device were present :confused: . I don't understand what's happening. This is probably more a question for the GNOME/Nautilus developpers but I would be happy to have any feed-back here.

Thank you, 

Cosmin

---

### Post by swerner on 2005-10-29
Desktop USB mounting/umounting is not a tidy feature in Ubuntu.  If you manually umount a partition and it gives you no error messages, that great, almost always it should be safetly unmounted.  
If you do get error messages and but the device disappears, there may be a problem. The safe thing to do is to open the command line Application>Accessories>Terminal and type:
sudo umount /media/usbdisk
Where /media/usbdisk may have to be changed to suit your system.

---

### Post by csaveanu on 2005-10-29
[QUOTE=swerner]Desktop USB mounting/umounting is not a tidy feature in Ubuntu.  If you manually umount a partition and it gives you no error messages, that great, almost always it should be safetly unmounted.  
If you do get error messages and but the device disappears, there may be a problem. The safe thing to do is to open the command line Application>Accessories>Terminal and type:
sudo umount /media/usbdisk
Where /media/usbdisk may have to be changed to suit your system.[/QUOTE]

Thank you, I'll try going through the Terminal next time :) . 

I did some more Google/forum research on the problem and you're right, USB mounting/unmounting is still problematic in Linux. Apparently data are not written immediately on disk when copying files. Instead it gets cached somewhere and is transferred **slowly** afterwards. Unmounting savagely, as I did, just did not allow the transfer to proceed, so *no data* on my flash drive. **This also explains the incredibly huge speed of the transfer - it is not the transfer speed itself that is shown in the progression message but the speed of caching the data for further writing to the disk. **

This is why data written to disk about half an hour ago where present: the transfer had been completed. In conclusion - people should pay attention to transferring large files on USB flash drives: _the visual feed-back on data transfer is just highly misleading_. A bug report should be send somewhere but I'm not sure where. Any idea?

Thanks,

Cosmin

---

### Post by swerner on 2005-10-29
I agree with you, mounting and file xfers need improvement on the user side of things.  I remember copying things to floppy, it would only show that it took a couple of seconds, however I never heard the floppy make it's "rrr-rrr" noise for more than a minute later.

Anyways, to file a bug report, first read [this]("https://wiki.ubuntu.com/HelpingWithBugs") then make sure your bug does not exist in this [list]("http://bugzilla.ubuntu.com/buglist.cgi?query_format=specific&order=bugs.resolution%2C+relevance+desc&bug_status=__all__&product=Ubuntu&content=usb+umount").

---

### Post by csaveanu on 2005-10-29
[QUOTE=swerner]
Anyways, to file a bug report, first read [this]("https://wiki.ubuntu.com/HelpingWithBugs") then make sure your bug does not exist in this [list]("http://bugzilla.ubuntu.com/buglist.cgi?query_format=specific&order=bugs.resolution%2C+relevance+desc&bug_status=__all__&product=Ubuntu&content=usb+umount").[/QUOTE]

Thanks for the links, I'll investigate the problem further before sending a bug report. For the moment I just posted these infos on the nautilus mailing list.

Cosmin

---

### Post by csaveanu on 2005-10-30
Hi everyone,

If you're interested, I sent a [bug report]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18674"). Hope someone finds a solution.

Cosmin

---

### Post by swerner on 2005-10-30
Cool, nice to see it's verbose.

---

