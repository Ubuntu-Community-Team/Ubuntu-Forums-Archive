---
title: "Security after a System meltdown"
date: 2009-03-10
forum: General Help
---

### Post by enlighten on 2009-03-10
My laptop went "phhttt" and died with no warning. I was running Ubuntu 8.04

I had a separate partition with my home directory. I popped out the hard drive, stuck it in a drive enclosure and attached it to another laptop and then got the 8.10 live CD so that I can see and move around files. Only the problem is that all the files are protected by SELINUX and I can't copy / read / write the files. 

Questions:
1. Can I read files with a Live CD or do I need to start off by installing Ubuntu before I do anything else?
2. I assume that I need to change the SELINUX policy to permissive - but is that the right way to do it?

Thoughts anyone?

(un)enlightened

---

### Post by dcstar on 2009-03-10
> **enlighten said:**
> My laptop went "phhttt" and died with no warning. I was running Ubuntu 8.04

I had a separate partition with my home directory. I popped out the hard drive, stuck it in a drive enclosure and attached it to another laptop and then got the 8.10 live CD so that I can see and move around files. Only the problem is that all the files are protected by SELINUX and I can't copy / read / write the files. 

Questions:
1. Can I read files with a Live CD or do I need to start off by installing Ubuntu before I do anything else?
2. I assume that I need to change the SELINUX policy to permissive - but is that the right way to do it?

Thoughts anyone?

(un)enlightened

```
gksudo nautilus
```

---

