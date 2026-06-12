---
title: "transmission will only start with sudo....other wize permission denied"
date: 2009-06-12
forum: General Help
---

### Post by bagwanram on 2009-06-12
Hi!

I was wondering if someone could help me!

I used to be able to open transmission from start-->internet-->Transmission

If I do that not I get the error : Failed to open the file /home/username/.transmission/gtk/lock for writing: permission denied

Also I can see my other windows computer on the network but none of its shares...
are these two related.

I did a little change in Users, I made my User(unity) part of the root group. did this do it?



Well thanks for any help!

J

---

### Post by colau on 2009-06-12
> **bagwanram said:**
> Hi!

I was wondering if someone could help me!

I used to be able to open transmission from start-->internet-->Transmission

If I do that not I get the error : Failed to open the file /home/username/.transmission/gtk/lock for writing: permission denied

Also I can see my other windows computer on the network but none of its shares...
are these two related.

I did a little change in Users, I made my User(unity) part of the root group. did this do it?



Well thanks for any help!

J

```

sudo aptitude purge transmission
sudo aptitude install transmission

```

---

### Post by bagwanram on 2009-06-16
hmm I still have to start trans with sudo...

---

### Post by lukeiamyourfather on 2009-06-16
It says there's a permission error and the file is in your home directory. Whatever you changed probably messed things up because you should have ownership over everything in your home directory regardless. There's only one root user for a reason. Cheers!

---

