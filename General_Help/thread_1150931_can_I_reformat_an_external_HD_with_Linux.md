---
title: "can I reformat an external HD with Linux?"
date: 2009-05-06
forum: General Help
---

### Post by cptrohn on 2009-05-06
Ok, I'm still new enough to linux that I have to ask about this...


I have a WD passport external HD that I stored some RealDVD files on when I used Window.... The thing is when I try to delete these files to trash I get an error saying the trash is full and empty it first.... (there is nothing in the trash folder at all) and then when I go to the individual files for the movies (I ripped about 3 of them to try out the RealDVD software to see how it worked) I get another error message saying that the files can't be removed at all....

I used to have all of my music and pictures on this HD, but as the collection grew the HD is no longer big enough to hold them... I want to get rid of the movie files and use this external HD with my older computer that I am running puppy on to speed that system up...

Sooo how would I go about doing this?  Is there a how-to somewhere on the internet that I am overlooking?

---

### Post by cariboo on 2009-05-06
Make sure you have gparted installed, it is in the repositories, then go to System-->Administration-->Partition Editor. You can manipulate partions as well as format them with this tool.

---

### Post by kryptikos on 2009-05-06
Often times on external devices (USB sticks are notorious for this) a hidden trash file is stashed on the devices. Usually something similar to .trash / .Trash / .trash-<numerical value> / .trash-<username>. So when you connect the device up be sure you mount it and switch inside your mount point and either from Nautilus (start it..then Edit -> Preferences -> View (tab) select show hidden files) or from terminal enter **ls -al** and look for that. 

If you are wanting to zero the device out you can use **dd** to blow the device away. There are lots of tutorials out there about how to format the device with dd (just google that). 

Or you can use fdisk to just repartition and write/format it with ext3 or whatever file structure you'd like.

[http://www.pinoytux.com/linux/disk-format-in-linux]("http://www.pinoytux.com/linux/disk-format-in-linux")

[http://www.eukhost.com/forums/f30/create-new-ext3-file-system-if-disk-added-system-972/]("http://www.eukhost.com/forums/f30/create-new-ext3-file-system-if-disk-added-system-972/")

Again, just be sure you are working on the device, as anything with dd or fdisk will destroy any data that does exist. You said you didn't care what was on the disk, but always good to be cautious before you hit "enter" :)

---

### Post by cptrohn on 2009-05-06
Thanks for the help guys!  Appreciated.

---

