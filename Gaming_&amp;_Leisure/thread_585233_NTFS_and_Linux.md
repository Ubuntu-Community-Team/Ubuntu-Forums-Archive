---
title: "NTFS and Linux"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by usarmykr on 2007-10-21
OK, Ive got a question.  I am dual-booting because windows SLI is 10 times better than Linux SLI for the moment.  I get all my games working in linux, but have better performance in windows, so I dual boot.  I just reinstalled windows and linux, and notice that I can read and write to my "data" partition which is formatted as NTFS.  How reliable is this writing?  I know that reading NTFS has been fine for awhile, but not sure on the writing aspect, last post I can find here is almost a year old.  I read on ntfs-linux.com(org maybe) that the NTFS read/write driver is included in the kernel now.  Can I install games, like WoW into my NTFS partition and play them with wine?  Or does wine have certain dependencies?  Does anyone have any experience with this?  Just want to know, in case I am doing something in linux and want to play a quick game of something.  If anyone knows anything about this, let me know please.  Thanks in advance for the help :P

---

### Post by Sockerdrickan on 2007-10-21
ntfs-3g

And if it is 10 times slower you should know another GPU doesn't add 100% fps :)

---

### Post by shad0w_walker on 2007-10-21
A. If you make claims, please back them up.
B. Ntfs 3g is your answer, you will need ntfs-3g and ntfs-config from the repos
C. At the moment wine doesn't like to directly access NTFS drives so it doesn't work accessing it directly from a NTFS drive

---

### Post by usarmykr on 2007-10-21
What claims? about the SLI? Its common knowledge that Linux sli is sad in comparison to windows, sli, show me the nechmarks that say linux sli is faster.  Ive got sli and in linux the money is wasted at the moment.  Thanks for the help :D

---

### Post by shad0w_walker on 2007-10-21
I didn't make any claim that SLI in Linux is better, however you made a claim about 10x slower, which i haven't seen any information about. So I don't need to show anything.

---

