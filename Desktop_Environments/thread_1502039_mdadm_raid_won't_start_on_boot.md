---
title: "mdadm raid won't start on boot"
date: 2010-06-05
forum: Desktop Environments
---

### Post by chocko on 2010-06-05
Running ubuntu 10.04 64 bit and am pretty new when it comes to playing with mdadm.

I can't seem to figure out how to make my array automatically start on boot. Im sure it's something simple but given that this is the first time I have used mdadm I am a bit lost.

mdadm.conf has the following entry:

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=34cbf536:e24400d6:ec021948:fcf3ea14

# /etc/fstab has the following:

/dev/md0 /export auto defaults 0 0

Not really sure when to go from here?

---

