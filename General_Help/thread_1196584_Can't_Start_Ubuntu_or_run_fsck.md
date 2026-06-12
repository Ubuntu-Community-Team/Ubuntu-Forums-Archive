---
title: "Can't Start Ubuntu or run fsck"
date: 2009-06-25
forum: General Help
---

### Post by apolloxi on 2009-06-25
So, I'm stuck in a loop.

I tried to start my Ubuntu partition up but it wouldn't. So, I figured it was time for recovery mode. The way it usually works is that it tries to load the file system, discovers it has error (duh) and does its own quick fsck before it tells me I need to do it manually. For some stupid reason, though, instead of taking me to a command line like it always did in the past, it now asks me to enter my root password to do maintenance or press CTRL+D to exit. I entered what I believe is my root password but it doesn't work, neither does any variation I can think of.

So, it wants me to run fsck, but it's prompting me for a password that either I forgot or the machine forgot, and it isn't taking anything.

So, how do I fix this loop I'm in? Is there a way to recovery my root password or change it? Or, is there a way to do fsck without having to deal with this at all? Any help would be appreciated.

Thanks in advance.

---

### Post by dcstar on 2009-06-25
> **apolloxi said:**
> So, I'm stuck in a loop.

I tried to start my Ubuntu partition up but it wouldn't. So, I figured it was time for recovery mode. The way it usually works is that it tries to load the file system, discovers it has error (duh) and does its own quick fsck before it tells me I need to do it manually. For some stupid reason, though, instead of taking me to a command line like it always did in the past, it now asks me to enter my root password to do maintenance or press CTRL+D to exit. I entered what I believe is my root password but it doesn't work, neither does any variation I can think of.

So, it wants me to run fsck, but it's prompting me for a password that either I forgot or the machine forgot, and it isn't taking anything.

So, how do I fix this loop I'm in? Is there a way to recovery my root password or change it? Or, is there a way to do fsck without having to deal with this at all? Any help would be appreciated.

Thanks in advance.

The true root account is disabled by default, you should try your normal password.

If that does not work, boot off a Live CD and do the fsck via the Partition Editor (right-click then Check).

---

### Post by Divider on 2009-06-25
did you try not entering a root password? i.e. blank.

also if memory serves me right you can just switch to tty1 or 2.

```
CTRL + ALT + F1 or CTRL + ALT + F2. etc.
```

If you can get to a terminal you can 

> sudo passwd root

---

