---
title: "Kernel Hackers Question"
date: 2009-03-01
forum: General Help
---

### Post by JoeCool1986 on 2009-03-01
Hey guys, I need to run some tests for a class on SLAB versus SLUB memory allocation, so I was wondering if there is an easy way to check which one your running kernel is using. I learned how to specify slab vs. slub in the config menu and then recompile the kernel, but I'm looking for a way to confirm the correct one is being used in the kernel after rebooting and running it. Is there any way to do that?

Thanks guys,
-Robert

---

### Post by snova on 2009-03-01
Have a look around in /proc, particularly meminfo and vmstat.

I'm only guessing here, but my first idea would be to check for the presence of fields that only one or the other allocator exports. What those are, you might have to look at source to be sure of...

---

### Post by damis648 on 2009-03-01
If you do
```
cat /proc/vmstat | grep -i slab
```
```
cat /proc/vmstat | grep -i slub
```
or
```
cat /proc/meminfo | grep -i slab
```
```
cat /proc/meminfo | grep -i slub
```
it will have output for whatever is being used (so if slub is used, the grep -i slab won't have any output):popcorn:

---

### Post by JoeCool1986 on 2009-04-20
Thanks for the help!:D

---

### Post by sdennie on 2009-04-20
Another way to do this would be to check the kernel config for the currently running kernel:

```

grep SL[AU]B /boot/config-`uname -r`

```

---

