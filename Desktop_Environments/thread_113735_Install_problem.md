---
title: "Install problem"
date: 2006-01-07
forum: Desktop Environments
---

### Post by trop on 2006-01-07
Hi,

Tried installing 5.10 today with no success. The install seems to hang at 'Starting partitioner' right at 41%.. I've tried acpi=off and all the other jazz suggested in the forum with no luck. I've tried installing 5.04 and killing it, I've even tried nuking and recreating partitions on term2 during, and before the hangup. 

Does anybody have any suggestions to try? Or perhaps something they've done to make it work?

Thanks,

-T

---

### Post by Ampersand on 2006-01-07
Have you tried burning the CD again (at about 12x speed)?

---

### Post by trop on 2006-01-08
Yeah, just tried burning at 12x and i got the exact same thing, at 41%.

Any other suggestions?

Thanks

---

### Post by lamego on 2006-01-08
If you are able to switch to term2 during the hangup then eventually you will be able to kill the hang process, if you have the parts manually created it may allow you to continue the install process, just an idea...

---

### Post by trop on 2006-01-08
Aye, that got me through that stage. Now I've just got to figure out what else happens in that step that i've 'skipped' and do what I manually.

Thanks again, Got any ideas what else is done there?

-T

---

### Post by trop on 2006-01-08
Well, this seems a little strange to me, but i'm sure it'll make sense to somebody.

After I went through the install (terminating the hanging process' from 'Starting the Partition manager') obviously some things didnt get setup properly ie: fstab was blank, etc. So I came back on da web to lookup the format for fstab. Anyway, when I went to reinstall ubuntu the install ran fine, no problems at all.

I also removed my flash drive before the final install.

Hope this can help somebody else,

Cheers,

-T

---

### Post by lamego on 2006-01-08
The partitioner allows you to create the partitions and filesystems, I guess it also sets the entires for /etc/fstab.
The next thing it should do is call the packager manager (I guess).

---

### Post by lamego on 2006-01-08
Did you had a prior linux instalation on that disk ? Maybe the partitioner was looking into an old /etc/fstab for existing partitions and that was causing it to hang ?

---

