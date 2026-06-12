---
title: "Unlocking a File &amp; Saving Files to Network Drive"
date: 2009-01-21
forum: Desktop Environments
---

### Post by PCHome on 2009-01-21
Ubuntu: 8.10 v2.24.1

From time to time I get files that seem to lock themselves for no apparent reason. Ubuntu sometimes completely locks up right in the middle of work requiring that I press Reset and it might be that these files were open when it happened but whatever the reason, how can I unlock them? I tried chown and chmod but neither will do it. In this case, the file name (and the path to it) has spaces in it so I presume I need to surround it by quotes. I changed directories to the file location and tried:

```
sudo chown don "File - Name.doc"
```

and

```
sudo chmod 777 "File - Name.doc"
```

It tells me in either case that it is "Not a directory." I wasn't aware that these commands would work only on a directory and I am sure that's not the case. Is there a switch I have forgotten?

Also, and more importantly, I cannot re-save files to my network drive in most applications. Some can do it but many cannot. That is, if I open an existing file and make changes, I need to save it to the desktop, delete the original file, and drag it from the desktop into the network drive folder when done. This is frustrating and VERY time-consuming. Is there a fix or, at least, a workaround?

Thanks,

Don

---

### Post by NTolerance on 2009-01-22
Your chown/chmod syntax is correct.  Those commands will work on both files and directories.  Those strange error messages and the lockups make me think that you might have hard drive or filesystem problems.  Are those documents stored locally or on a network drive?  Try and post some more info about your network setup, such as what type of network share you are using and how it's mounted.

---

### Post by PCHome on 2009-03-04
I haven't tried the locked file for a while but I am still having the issues in saving files.

The files are stored on a network drive and the network itself is just a usual home network with a router and RJ45 jacks in each room. The drive is a D-Link SATA unit with two 500gig RAID drives formatted by default for Linux. I am not in Linux at the moment so don't have the exact information available but the drive is being auto-mounted. After someone suggested some changes to the auto-mount line, there have been improvements but it's still not working properly.

Interestingly, the "save" issue now seems to involve mainly GIMP as I cannot save updates to a file that already exists. After prompting to confirm that I am about to overwrite the file, it still gives the "Not a directory" error which makes no sense.

In the text editor, I can now save them but I get messages that the file was changed outside of the editor when it was not. I am always asked when saving if I want to Reload or Save Anyway.

I just realized that I wasn't getting email notification and didn't know that there was a reply. Most other forums I use have this enabled by default.

---

