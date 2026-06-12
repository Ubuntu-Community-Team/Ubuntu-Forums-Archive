---
title: "Suspend and hibernate are funky"
date: 2007-02-17
forum: Desktop Environments
---

### Post by NiksaVel on 2007-02-17
Hey all,

I have a problem with suspend and hibernate on my laptop running ubuntu edgy...  and everything "Just worked" with dapper...


with suspend, when I turn the comp back on I have to disable networking and than re-enable it to get network access...   and I only manage to get wired back...  for wireless I have to reboot.  eth1 (wireless) doesn't even appear with ifconfig...


as far as hibernate is concerned, I am not even able to shut the comp down... I get an error msg, previously about not enough swap - so I increased it, but I still see a msg before I get returned to desktop - however the msg is visible for only a fraction of a second and I can't read it - is there a log somewhere?


thanks!

---

### Post by z600 on 2007-03-03
I'm having the same problem. I can restart the wirless connection as follows:

sudo ifdown eth1
sudo ifup eth1

assuming eth1 is your wireless adaptor.

It would be nice to be able to run this as a script from a file that is envoked when the computer jumps out of suspend mode.

I also found that I need to unmount and remount network shares on resume.

---

### Post by NiksaVel on 2007-03-03
or better yet... have this fixed in the next ubuntu release :)

---

