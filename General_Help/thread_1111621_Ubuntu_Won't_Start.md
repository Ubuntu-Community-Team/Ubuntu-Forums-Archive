---
title: "Ubuntu Won't Start"
date: 2009-03-30
forum: General Help
---

### Post by jasper28 on 2009-03-30
I have a dual boot system that I've been using for a while now and I recently tried to edit some system files.  Ubuntu wouldn't let me, and I figured that I didn't have permission.  So I went into users and groups to try to configure the permissions for my account.  In doing so, I changed the home directory of my account to /root as well.  I need to change it back so I can login.  How do I do this without being able to log in?

---

### Post by xenophed on 2009-03-31
rescue disk (puppy linux works good) mount your partition with linux and edit the file [mount point]/etc/passwd look for your user name in a line that looks like this:
[your user name]:x:1000:1000::/root:/bin/bash
change it where it says '/root' to '/home/[your user name]
that is why there called rescue disk:)

---

### Post by jasper28 on 2009-03-31
Thanks, I'll try that.

---

### Post by jasper28 on 2009-03-31
It worked!  I'm typing this from ubuntu now. Thank you!

For some reason System Rescue CD didn't work for me, even though stuff like this is what it's made for.  I had to use Puppy instead.  It showed the text file differently in System Rescue than in Puppy Linux even though they use the same text editor.  Weird.

---

