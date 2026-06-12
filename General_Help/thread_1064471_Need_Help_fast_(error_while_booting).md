---
title: "Need Help fast (error while booting)"
date: 2009-02-08
forum: General Help
---

### Post by chaotzu on 2009-02-08
ok so this just randomly happened after restarting from windows and trying to boot to Ubuntu. It shows the progress bar and Ubuntu logo then clears it and just shows text.

several errors that say similer things to: EXT3-fs error (device sdb5): ext3_get_inode_loc: unable to read inode block - inode=2927009, block=11730946"

also "init: Unable to execute "/bin/sh" for rc-default: Input/output error"
"init: rc-default main process (2495) terminated with status 255"

I have some homework that is due in about 3 hours (of course). I appreciate any help I can get. (if I could find where my homework is on the hd too that would work for now. It is saved to default folder terminal opens to)

---

### Post by chaotzu on 2009-02-08
I've searched google, but usually people mess their own files while trying to mess with it. Not that it randomly happens. Any suggestions?

---

### Post by racie on 2009-02-08
I had a boot problem some time ago when I was trying to fix a problem on Xubuntu.  When trying to boot Xubuntu, it brought me to a black screen and wanted me to type something.  I really don't know.  Anyway, the only advice I can give is to uninstall Ubuntu.  Sorry I can't be of more help, but I wouldn't want to leave you unanswered.

---

### Post by chaotzu on 2009-02-08
well think you anyways. I'm reinstalling, I'm resolved to trying to do the work over. It's about my only choice

---

### Post by racie on 2009-02-08
Yeah, sorry about that.  Good luck with your work and everything.

---

### Post by pbotros1234 on 2009-02-08
You don't need to!

Look up Ext2 IFS on windows, its something that can be used to read your EXT3 partition from windows. THis way, you should be able to look through the partition and find your work, and then copy+paste it into your windows drive.

Oh and the default location for the terminal opening is /home/(your username)/

---

### Post by personjerry on 2009-02-08
two words: live cd

it can browse files on your hard drive.

---

### Post by mefistofeles666 on 2009-02-08
When restarting it gives you a choice to access the menu by pressing  Esc key. when you do that it will give you several booting options including recovery mode. Try all of them and one of them might let you use  ubuntu somewhat normally. I'm having almost the same problem as you and after a while found I could run ubuntu this way as I fix the problem.

---

### Post by chaotzu on 2009-02-08
IFS kept having errors, and when I couldn't find my homework file when I was browsing with live cd.

---

### Post by Vadi on 2009-02-08
I'd run a disk check ASAP. "unable to read inode block" means just that - unable to read data from your HD. Unluckily for you, the data there is what's needed to boot Ubuntu.

Since the hd got corrupted here, it might start breaking down in other places :\

---

