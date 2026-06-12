---
title: "Having trouble interpreting fsck results"
date: 2009-04-23
forum: General Help
---

### Post by Baasha on 2009-04-23
I have been having some instability recently, particularly with Firefox and Thunderbird.  So I ran a fsck on my system.  The results I got were:

bob@ubuntu:~$ fsck -A
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=d1506f7b-b5d3-4eec-bef0-226f8233f27f'
bob@ubuntu:~$ 

I am not sure what to do with this information or even if it has any connection to the problems I am having.  Can anyone advise?

BTW I am running Ubuntu 8.04

---

### Post by sdennie on 2009-04-23
I would say use "sudo blkid" and figure out the /dev name for that UUID and try running "fsck -f" on that partition while booted into a Live CD or a system restore CD.

---

