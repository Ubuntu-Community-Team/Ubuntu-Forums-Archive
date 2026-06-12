---
title: "auto home help please"
date: 2009-05-20
forum: General Help
---

### Post by slyost on 2009-05-20
I am trying to automatically mount home directories on a Ubuntu 9.04 client.  Home directories are stored on a SUN NFS server.  I can successfully accomplish this task with either faculty or students at one time but not both together.  Home directories are stored either in /export/home/faculty or /export/home/students.  Is there a way I can create my auto.home file to manage two different directories on one server.  I found a way to use the same directory name on two different servers but not what I want.  My auto.home now reads:  *    sadok:/export/home/faculty/& and mounts the faculty just fine.  If I change it to the following:  *    sadok:/export/home/students/& it mounts the students fine.  Can I do both at the same time.

---

### Post by Jonnox on 2009-05-20
Have you tried to mount the home directory so you can access both? Like, instead of mounting .../student/& and .../faculty/&, couldn't you just do ../home/& and then both should be accessable (that is of course assuming that there are no other directories in the ../home/

---

### Post by slyost on 2009-05-20
> **Jonnox said:**
> Have you tried to mount the home directory so you can access both? Like, instead of mounting .../student/& and .../faculty/&, couldn't you just do ../home/& and then both should be accessable (that is of course assuming that there are no other directories in the ../home/
 
Tried that allready, didn't work.  Thanks for the suggestion though.

---

### Post by slyost on 2009-05-20
I am thinking there may be a way to check the group membership of the user before tring to mount the home directory and use the appropiate mount point to mount their home directory.  i.e. If a users primary group is student use auto.student and if the primary group is faculty use auto.faculty or something like that.  Or if it does not find it in the first entry use the second in auto.home.

---

### Post by Jonnox on 2009-05-22
Yea, just have a (shell) script determine that. I wonder why it doesn't let you access them both though by mounting it to home... Have you tried to make a different folder, then just make a symbolic link from home to that, and then you can mount to that folder?

Sorry I couldn't be of more help :(

---

