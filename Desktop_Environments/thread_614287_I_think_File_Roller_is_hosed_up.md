---
title: "I think File Roller is hosed up"
date: 2007-11-15
forum: Desktop Environments
---

### Post by jsbarnes1002 on 2007-11-15
Most ZIPs that I open result in File Roller crashing with:

An error occurred while loading the archive.

When I click on "Command Line Output" it says:

Segmentation fault (core dumped)

I've tried removing/re-installing it, but it fails.  When I click on "details" there are numerous "Segmentation fault" messages.  I downloaded file-roller-2.18.4.tar.gz, but I've been unable to install it.  When I sudo ./configuration, it says the compiler can't make the EXE file.

Please put me on the right path.

Thanks,
Jeff.

---

### Post by tzulberti on 2007-11-16
Two questions:
-> Have you tried to install another file manager?
-> Those this happens with any other type of file?

---

### Post by spupy on 2007-11-16
Doesn't file-roller use external archivers? If so, the problem is in the zip package(s). As tzulberti said, try different file types.

---

### Post by jsbarnes1002 on 2007-11-19
Sorry, but I'm an Ubunto newbie.  I'm not sure I know what you mean by "try a different file manager."  I'd much rather fix File Roller if possible.

---

### Post by spupy on 2007-11-19
You can try again reinstalling. Reinstall these two packages: ''file-roller" and "zip".  But here is how to do it! Open Synaptic and find the two packages. Right click on each of them, and from the context menu select "Mark for complete removal". Apply the changes, and then install file-roller normally.

---

### Post by jim_p on 2007-11-19
Try reinstalling and if possible please try another compressed file manager like xarchiver.
This is done just to check if the problem lies on the file-roller or the zip.

I sometimes have problems opening password protected .rar files with file roller, so I have xarchiver as a "backup plan"

---

### Post by jsbarnes1002 on 2007-11-20
> **jim_p said:**
> Try reinstalling and if possible please try another compressed file manager like xarchiver.
This is done just to check if the problem lies on the file-roller or the zip.

I sometimes have problems opening password protected .rar files with file roller, so I have xarchiver as a "backup plan"

I successfully uninstalled bzip2, but it errors out when I try to uninstall file-roller.  Now, whenever I try to install/uninstall something, I get dpkg errors.

HELP!  It's going from bad to worse.

---

### Post by jsbarnes1002 on 2007-11-20
> **jim_p said:**
> Try reinstalling and if possible please try another compressed file manager like xarchiver.
This is done just to check if the problem lies on the file-roller or the zip.

I sometimes have problems opening password protected .rar files with file roller, so I have xarchiver as a "backup plan"

The error is subprocess post-installation script returned error exit status 139.

---

### Post by jsbarnes1002 on 2007-11-26
I resolved the problem by re-installing Ubuntu :-(

---

### Post by LoTech242 on 2007-11-27
I tried uninstalling and re-installing file-roller and it still doesn't work for me.
here is the command line output:

Write error in the file /home/lotech/Temp Download/(audiobook) Alan Watts - Teaches Meditation/Alan Watts - Teaches Meditation.mp3 [R]etry, [A]bort 
Write error in the file /home/lotech/Temp Download/(audiobook) Alan Watts - Teaches Meditation/Alan Watts - Teaches Meditation.mp3
Inappropriate ioctl for device

what is ioctl?
any ideas?

---

### Post by LoTech242 on 2007-11-27
nevermind.... I was just being stupid. My HDD was full :]

---

### Post by Xvani on 2008-03-14
No, you weren't being stupid.
The error message was stupid..

Same problem here. Now I saw disk was full =)

---

### Post by cal_zlone on 2008-07-18
Mine also says "Inappropriate ioctl for device".  But my HDD is NOT full.  What gives?

---

