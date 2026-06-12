---
title: "Filename &quot;????????&quot; under KDE 4"
date: 2008-06-22
forum: Desktop Environments
---

### Post by xolot1 on 2008-06-22
Im running Hardy with KDE4.1 alpha/beta.  After working with the Arduino IDE folder, I was left with two files that are represented only by "????".  This occurs under bash, as well as the KDE file managers.  I dont want the files around, but I'm not sure how to delete them.  Dolphin returns:

"The file or folder /home/willi/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; does not exist"

Bash does not recognize the file either.

I have a screenshot, and it can be found here:
[http://flickr.com/photos/xolot1/2600759101/sizes/l/](http://flickr.com/photos/xolot1/2600759101/sizes/l/)


How do I delete these files?
Thanks!

---

### Post by Zorael on 2008-06-23
And it's not the filesystem acting up? To force it to check at next boot, do this in a terminal.
```
$ sudo touch /forcefsck
```

---

### Post by xolot1 on 2008-06-23
Thanks for the suggestion.
I created that file, and a check was performed.

Actually, now that I think about it, my home directory is located on a different partition from my root partition. I'll try this procedure again for my home directory partition.

---

