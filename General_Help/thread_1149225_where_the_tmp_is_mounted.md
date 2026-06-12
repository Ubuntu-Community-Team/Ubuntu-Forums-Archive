---
title: "where the tmp is mounted"
date: 2009-05-05
forum: General Help
---

### Post by Shady3D on 2009-05-05
i want to know whether the tmp is mounted to the HDD or the ram?

and the other part of the question depend on the answer

---

### Post by kpkeerthi on 2009-05-05
You can find that using ```
mount
``` command. Or check the contents of /etc/fstab. If there is no entry for /tmp, then it is part of your / (root)

---

### Post by Shady3D on 2009-05-05
i didn't mount it but i thought maybe its by default.

so anyway the other question is, how to mount tmp to ram and what is the disadvantages of this, and i want to know also what will happen to firefox

---

### Post by kpkeerthi on 2009-05-05
> **Shady3D said:**
> i didn't mount it but i thought maybe its by default.

No. It is not the default. Your /tmp will be on the same partition as your /

> 
so anyway the other question is, how to mount tmp to ram

See [http://ubuntuforums.org/showthread.php?t=1054129]("http://ubuntuforums.org/showthread.php?t=1054129")

> 
and what is the disadvantages of this
You need plenty of RAM. How much? That cannot be quantified. It depends on your usage pattern. If you use an application that needs a lot of /tmp space, then you need to make sure your /tmp is sufficient enough. 

> 
and i want to know also what will happen to firefox :confused: It may crash when your /tmp gets filled up. Honestly, I have no clue.

---

### Post by Shady3D on 2009-05-05
so do u think a 4GB of ram on 64bit machine will do it, because i rarely use half of it

---

