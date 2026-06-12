---
title: "Is it possible to make an Image of my entire current ubuntu system for backup?"
date: 2009-05-26
forum: General Help
---

### Post by Mashuteichou on 2009-05-26
Here is what I need it for.  I am going to be selling my computer, but I don't want to redo Linux because I have many hours into getting it to where its at now.  So what I want to do is make an image of the partition that I have, then transfer it to another hard drive.  The HD will be a different size, Im not sure if that matters.  

Is this worth it to do that, or is it easier just to wipe it all and redo it?

---

### Post by chriskin on 2009-05-26
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

remastersys seems to be able to do it for you
(it  might be in the repositories as well)

i never use apps like that though, clean installs always give me the opportunity to make the system better than it was before , though almost 99% of the people out there would tell you that it is worth it

---

### Post by nebileix on 2009-05-26
try clonezilla. it should get the job done. as for different hd size, it'll be different as wat i remember. but there are ways to get around it which i cant recall now.

[http://www.linux.com/archive/feature/115208]("http://www.linux.com/archive/feature/115208") theres instruction to do it on these link.

and regarding different size issue [http://www.linuxquestions.org/questions/linux-newbie-8/clonezilla-clone-disk-to-image-when-restore-from-image-to-destination-hdd-problem.-630039/]("http://www.linuxquestions.org/questions/linux-newbie-8/clonezilla-clone-disk-to-image-when-restore-from-image-to-destination-hdd-problem.-630039/")

---

### Post by maheshasolkar on 2009-05-26
If you plan to put the image on a different computer, I would most definitely advise against it - unless the new computer has exactly the same specs (hardware especially).

I would back up the following folders (Others can suggest more if needed):

[LIST]
[*]/etc : It holds all your configuration data
[*]/home : Your home directory (which can be moved to its own partition, while you are at it)
[*]/var/www : If you have any web pages
[*]/opt : If you installed any software that goes to /opt
[*]Any other directory you added
[/LIST]

Then I'd reinstall Linux on the new computer. After the installation is done, copy the /home folder data into your new computer.

I'd not copy the other folders in their entirety. I'd copy configuration files as needed.

Having said that, you can create images with Partimage, which you can find on SystemRescueCd:

  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by VMC on 2009-05-26
> **maheshasolkar said:**
> ...

Having said that, you can create images with Partimage, which you can find on SystemRescueCd:

  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)If he's using Ext4 FS, then Partimage won't work. Use partclone. It's available on Clonezilla and the soon to be released Pated Magic distro.

---

### Post by Alekz_ on 2009-05-26
You can "dump" your system!

Read the man:

```
man dump
man restore
```

No additional apps needed!

---

### Post by Mashuteichou on 2009-05-26
I think those tools would work.   But the points about making it better and hardware changes make sense.  

Im going from a laptop to desktop.  So everything will be different, even the graphics card.  And yeah, that wouldn't be the best idea to put an OS that is configured to something completely different.  So, I guess I don't want to make an image now.  lol.

---

