---
title: "How do I delete a raid array? md0"
date: 2005-08-12
forum: Desktop Environments
---

### Post by smack on 2005-08-12
I created md0. I tried stopping it and then deleting it but mdadm doesn't appear to have a delete command. When I 'cat /proc/md0' it states that the raid is still set up but inactive. I want to set up a new array with different disks. I guess if I could leave md0 created but just swap in totally different disks that'd be ok too.  :-? 

How do I delete this thing? I've read a few usenet posts saying that mdadm doesn't let you delete the arrays, only create them.  ](*,)

---

### Post by smack on 2005-08-12
I got it...

I couldn't get rid of md0 because I had one of the disks in that raid mounted elsewhere.

What a rookie mistake.  :-#

---

