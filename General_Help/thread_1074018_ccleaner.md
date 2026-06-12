---
title: "ccleaner"
date: 2009-02-18
forum: General Help
---

### Post by orc_dragoon on 2009-02-18
Would there be a point to install CCleaner? Sorry Im such a noob.


**If you Don't Know What it is Google It!**

---

### Post by yther on 2009-02-18
CCleaner is a Windows utility (and a very useful one at that).  It will do nothing for your Linux system, and in fact it wouldn't even run unless you had [WINE]("http://winehq.org/") or something.  :)

---

### Post by orc_dragoon on 2009-02-18
Thanks. Is there any programs similar for linux. To help "unclogg" my machine?

---

### Post by Old_Grey_Wolf on 2009-02-18
See if this link helps. [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by konqueror7 on 2009-02-18
i use bleachbit, its similar to ccleaner. but i've stopped, i'm doing my maintenance manually now...;)

---

### Post by mb_webguy on 2009-02-18
From Wikipedia (I had to look it up):> CCleaner allows the user to remove unused temporary files from Internet browsers and other supported applications along with browsing history, cookies, recycle bin, and AutoComplete form history. It allows for the cleaning of the recycle bin, memory dumps, file fragments, log files, system caches, application data, and various other data. The program also includes a Registry Cleaner to locate and correct problems in the Windows Registry such as missing shared DLLs, unused file extensions and application paths.

I can't think of any single application that is the equivalent of this for Linux, but in general Linux just doesn't get a cluttered as Windows.

Temporary files in Linux are generally stored in the /tmp folder, which is cleaned out automatically when you reboot.

You can easily remove cookies and other temporary files from Firefox, with Tools->Clear Private Data.  You can clean your Trash in either the file manager or with the panel icon.

Linux doesn't use a registry or DLLs, and if you use Synaptic, Add/Remove Applications, or apt-get to install software, you don't have to worry about orphaned application paths.

You can use the commands "sudo apt-get autoremove" and "sudo apt-get autoclean" to automatically remove unused and unneeded software packages.

EDIT:  I wasn't aware of [bleachbit]("http://bleachbit.sourceforge.net/"), which konqueror7 mentioned.  It sounds a bit like ccleaner.  You might want to look into it.

---

### Post by orc_dragoon on 2009-02-18
> **konqueror7 said:**
> i use bleachbit, its similar to ccleaner. but i've stopped, i'm doing my maintenance manually now...;)

Thanks I have bleachbit installed now and its working great,

---

### Post by solwic on 2009-02-18
> **Old_Gray_Wolf said:**
> See if this link helps. [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Thanks for that link.  I just went through a couple of the steps.  I didn't realize how many residual packages I had.  

:)

---

### Post by orc_dragoon on 2009-02-18
Im glad this is helping more than me.

jrock. Bleachbit seems pretty good you should try it.

---

