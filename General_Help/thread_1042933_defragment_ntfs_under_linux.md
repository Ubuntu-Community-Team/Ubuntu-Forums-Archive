---
title: "defragment ntfs under linux"
date: 2009-01-18
forum: General Help
---

### Post by pacman401 on 2009-01-18
Hello everyone.
is existing program natively running under under linux ad defragmenting windows partition system especially ntfs ?

---

### Post by Takmadeus on 2009-01-18
Well, I ask you, why not defragment the ntfs partition from inside windows?

The included defragmenter is not very efficient, but if you check defraggler you might just find what you need :)

---

### Post by pacman401 on 2009-01-18
> I ask you, why not defragment the ntfs partition from inside windows?
Why ?
Because system files running in windows like a explorer.exe , sms.exe svhosts.exe etc are locked when are executing , and that MTF table that big space with is really empty space is preventing form fully defragmenting my ntfs partitions , eve if files are fully defragmented that MTF space is preventing to relocate files continuous.

a boot-time defragmentation isn't sufficient too for me 

so that why i need to defragment ntfs partitions under linux , there will be no locked files to relocate and MTF space will be no present(because is visable under windows/boot-time defrag runs some windows componentes too) so in fact files can be relocate continuous and windows create new MTF space at the end of files

---

### Post by adamlau on 2009-01-18
VirtualBox, Windows XP, Diskeeper/PerfectDisk/Vopt, Mount, Defrag, Done.

---

### Post by pacman401 on 2009-01-18
so I will explain how it will be if i do in your way 
VirtualBox->run/emulate-> Windows XP -> windows will lock system files and active MTF space --> so Diskeeper will not be able to fully defragment partitions

---

### Post by Takmadeus on 2009-01-18
Interesting reason.... Well, unfortunately I would not know how to help you in there, although it would be a great project

---

### Post by theozzlives on 2009-01-18
I don't know if this will help but try:
[http://www.bootdisk.com/]("http://www.bootdisk.com/")

---

### Post by NickNackGus on 2011-02-28
> **pacman401 said:**
> so I will explain how it will be if i do in your way 
VirtualBox->run/emulate-> Windows XP -> windows will lock system files and active MTF space --> so Diskeeper will not be able to fully defragment partitions

Another reason against using a VM to defrag a partition is that it is not easy to emulate an operating system that uses n% of your disk! However, if you set up a VM with a virtual hard disk, then you can mount the Windows partition as a external hard disk of sorts, and defrag it without running from it. This works with physical machines too. (I am not going to be held responsible if this messes something up, make a backup first and prove/disprove me here before trying yourself.)

However, it would be nice to have a LINUX (or Debian) application to defrag NTFS. Less trouble, and I use Linux more than Windows, so I could just leave a defragmenter running until I am ready to use the NTFS partition...several months later :).

---

### Post by mringer on 2011-05-24
My reason for wanting to defrag a ntfs partition under Linux is that the
Windows defrag tool is amazingly slow. I was hoping that a Linux defragger
would work in a logical fashion without all this knocking off for a beer.

---

