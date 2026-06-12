---
title: "Absolute Log-in problem"
date: 2007-01-07
forum: Desktop Environments
---

### Post by Skerit on 2007-01-07
My installation won't let me log in - in any way!

Not graphically, not in the terminal, ... 

It's a very strange problem, I get all kinds of weird stuff on my screen like:

inode_loc+0x251/0x340 [ext3]
current_fs_time+0x50/0x60

and so on.. even some hex "code" which is a few lines long, and the last line is:

<7>eth2: no IPv6 routers present

If I try to log in again, after the first attempt, it'll just freeze... I can go to another terminal or the gdm, by using the ctrl+F keys, but that's it... 

I've tried the ...-386 kernel and the generic one, but both have the same problem :-k

(Oh, I just used the single-user mode.. why does it auto-log-in to my root account without asking a password? Isn't that kinda dangerous? :s)

anyway, in the single-user mode I tried to enter my home directory and *shudder* it complains of a segmentation fault!

so I guess my hd crashed! That's veery unfortunate as it's my newest (and only Serial-ata) HD

I'm running e2fsck on it now but, even though the verbose mode is enabled, it's not syaing anything (yet the system is responsive ...) 

What to do now?

---

### Post by Skerit on 2007-01-07
Ok, I read the post on "Why are you not getting any reply's to your post" or whatever it's called but I'm not even getting views soo... I took the liberty to bump the post, sorry :s

---

