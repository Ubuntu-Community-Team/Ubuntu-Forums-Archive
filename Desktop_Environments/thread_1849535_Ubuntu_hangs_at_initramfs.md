---
title: "Ubuntu hangs at initramfs"
date: 2011-09-24
forum: Desktop Environments
---

### Post by vra5107 on 2011-09-24
Hi

           My ubuntu standalone installation fails during startup. Now I do have windows installed in parallel, but Ubuntu owns the boot record. 

I have tried going back to older versions of ubuntu, but they all see the same problem. I have read online that this may happen when there is a failed sudo apt-get update since linux sets a flag of some sort. Is there a way to reset this ?

I am unable to get past this , any help is appreciated.

---

### Post by vra5107 on 2011-09-24
Ok

        I was able to run live cd and start an OS. I have tried the command below without any success.

```

sudo update-initramfs -u
update-initramfs is disabled since running on read-only media

```

Is there a way to fix the initramfs on existing ubuntu installation using the live cd?

---

### Post by vra5107 on 2011-09-24
Well

          This was already solved in another post. I was able to fix my problem looking at that post as well.

[http://ubuntuforums.org/showthread.php?p=11282550#post11282550](http://ubuntuforums.org/showthread.php?p=11282550#post11282550)

Thanks to anybody who has looked into this.

Venkat

---

