---
title: "Problems updating on Inspiron 8000"
date: 2008-12-23
forum: General Help
---

### Post by sexcopter on 2008-12-23
Hi,

I just installed Ubuntu 8.10 on an old Inspiron 8000. It all seems to work fine (after fixing a video/resolution issue), except that getting the system up-to-date has thrown up a few errors. I can't really decipher the output, except there are error codes, and I'm not sure what they indicate. Have run apt-get update and apt-get upgrade repeatedly and get the same output every time.

I'm hoping someone can help me and make sense of what the problem here is (and ideally what I can do to resolve it). 

Below is the output:

[http://paste.ubuntu.com/91127/](http://paste.ubuntu.com/91127/)


Thanks a bunch,

James

---

### Post by Xiong Chiamiov on 2008-12-24
It seems from a bit of Googling that your best bet is to reinstall grub.

---

### Post by sexcopter on 2008-12-31
> **Xiong Chiamiov said:**
> It seems from a bit of Googling that your best bet is to reinstall grub.

Thanks, your suggestion seems to have worked! I think it's to do with the files in /var/lib/dpkg/info/

I'm now scratching my head for a couple of new reasons. 

Firstly, how has it come to be that there are thousands (yes, thousands!) of packages with missing information (eg "dpkg: serious warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed.") I'm guessing that there was some major corruption on the filesystem, though e2fsck seemed to give the ok on boot-up.

Secondly, how can I rectify this? I've noticed that reinstalling the offending packages fixes it, but I haven't the time to go through and reinstall them one-by-one. Is there a way to automate this? I'm not familiar with regex, but maybe can use it to get the packages names from the error list and then feed that into apt-get install --reinstall?

Thanks again, any thoughts on this?

James

---

