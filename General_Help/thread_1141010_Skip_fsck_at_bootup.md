---
title: "Skip fsck at bootup"
date: 2009-04-28
forum: General Help
---

### Post by Andreas1 on 2009-04-28
hi,
when the boot splash is enabled, you can skip the routine check of a file system with ESC, but with the boot splash disabled nothing seems to stop fsck. can someone give me a hint?

---

### Post by Andreas1 on 2009-04-30
bump

---

### Post by dcstar on 2009-04-30
> **Andreas1 said:**
> hi,
when the boot splash is enabled, you can skip the routine check of a file system with ESC, but with the boot splash disabled nothing seems to stop fsck. can someone give me a hint?

```
man tune2fs
```

This issue has hundreds of posts already - all searchable.

---

### Post by Andreas1 on 2009-05-01
i did look through [these]("http://ubuntuforums.org/search.php?searchid=58848357"), but didn't find my answer. man tune2fs is not helping me either. maybe i wasn't very clear, i don't want to change any fsck options, i want to know how to kill it in case of being in a hurry and not having time for the routine check.

---

### Post by cariboo on 2009-05-01
It takes less than 5 seconds to check my 150Gb home directory, what's the rush?

---

### Post by dcstar on 2009-05-01
> **Andreas1 said:**
> i did look through [these]("http://ubuntuforums.org/search.php?searchid=58848357"), but didn't find my answer. man tune2fs is not helping me either. maybe i wasn't very clear, i don't want to change any fsck options, i want to know how to kill it in case of being in a hurry and not having time for the routine check.

The option to skip it was added to that interface, it the fsck is too inconvenient then you must use the tool I outlined to change your settings.

---

### Post by Andreas1 on 2009-05-01
> **cariboo907 said:**
> It takes less than 5 seconds to check my 150Gb home directory, what's the rush?

i mean when it says something like "/dev/sda9 has been mounted 100 times without being checked, check forced, press esc to skip" or something like that. with my 106GB ext3 data partition this takes a few minutes.

> **dcstar said:**
> The option to skip it was added to that interface, it the fsck is too inconvenient then you must use the tool I outlined to change your settings.

so i take it there is no option to kill fsck once its has started (during the booting i mean)? i won't change any options because in general i want those routine checks. i was looking for the equivalent to the "press escape to skip" option that is offered in that situation if the boot splash is on.

my concern was something like the following scenario:
"hey, i am late for that train, can you quickly look up from wich platform it departs online?"
"sure, wait a second"
...booting...fsck starts...
"what is taking so long?"
"sorry, i don't know how to skip the routine drive check, we have to wait"

---

### Post by pzico on 2010-08-02
> **cariboo907 said:**
> It takes less than 5 seconds to check my 150Gb home directory, what's the rush?

Less than 5 seconds? On my computer it takes some 8 minutes for 300Gb. However when operating system has started and I move big files and so, I don't see any performance problems. Why does fsck then take forever? Would be nice to be able to skip it if hurry.

---

