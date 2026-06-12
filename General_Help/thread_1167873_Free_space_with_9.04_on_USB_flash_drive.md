---
title: "Free space with 9.04 on USB flash drive"
date: 2009-05-23
forum: General Help
---

### Post by iUser on 2009-05-23
Hello,

I'm using Ubuntu 9.04 (Desktop Edition) on a 4 GB USB flash drive. I originally installed 8.10, but yesterday evening I upgraded to 9.04. First, with 8.10, I had 1,3 GB free space on the flash drive, but now with 9.04, 5 minutes ago I had 250MB free, now it's 330 MB, and sometimes, even if I do nothing, it's suddenly 328 MB, decreasing. Now I've got some questions:

- Is this normal? :D If not, what can I do that Ubuntu doesn't eat up all my free space? Can this really happen?
- Why does Jaunty use so much more space than Intrepid?
- Can I uninstall things for freeing more space? And, if yes, which ones and how can I do this?

Yes, I'm really new with Ubuntu... ;-)

Thanks, 

iUser

---

### Post by iUser on 2009-05-23
May I *push* it already? :D I don't know if and after which time pushing is allowed :D Please tell me ;-)

---

### Post by iUser on 2009-05-24
Okay, I solved the problem myself.

```
sudo apt-get clean
```

cleaned up 600 more megabytes, I think the 300 MB more than Intrepid are because of the system is Ubuntu Jaunty now :D

---

