---
title: "Some mysterious bugs in Jaunty...Firefox and now X"
date: 2009-05-22
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-22
Hi, I'm running Jaunty Jackelope on my PC and have experienced a couple of probs within the past few days...

The first one has to do with Firefox..I can't remember it occuring on any other program. When running it in the usual way, it shuts down all of a sudden without warning. This tends to happen at times when loading a page in most cases, so I thought it could be that...But then it's not a fault of the server or anything, the page loads again afterwards and in somecases, I've loaded it before. This even happens to the most common sites I visit, ubuntuforums.org and facebook.com

The second problem happened about 5mins ago. I was checking out something on the archlinux site (for experimental purposes, not to give up ubuntu! :D). I was running Firefox, Rhythmbox and Pidgin...I don't think these apps have anything to do with the problem anyway..at least maybe firefox, IF, any app *was* responsible, coz that was the main process at the time. Uhh, I clicked this link at archlinux.org and after a 2 or 3 second delay, my screen went blank. Then, I saw the load info that's displayed onscreen when X loads at boot up or when logging out. After about 10-20 seconds, maybe more, the login manager became visible and I logged in once again.

If it's any help, I'm running the 2.6.30-rc6 kernel. I was using the rc5 about two days ago. The reason for this is coz, for one thing I like to run latest software like rc's and I'm using Intel's i845 video. Thanks for any replies on this...

---

### Post by b@sh_n3rd on 2009-05-22
OK, now Pidgins giving the same trouble as firefox...sudden crash..

---

### Post by wpshooter on 2009-05-22
Seems like to me that I have seen in various forum post where it is mentioned that there are problems with Intel video under Jaunty.

---

### Post by b@sh_n3rd on 2009-05-22
So you mean it's a prob with my video? But how can my video problem trigger an error in programs like Firefox and Pidgin? How about the rc kernel? could that be a prob? I think I'll test with the 2.6.29 kernel release later on...

---

### Post by wpshooter on 2009-05-22
Try reading this post.

[http://ubuntuforums.org/showthread.php?t=1136738&highlight=intel+video+jaunty](http://ubuntuforums.org/showthread.php?t=1136738&highlight=intel+video+jaunty)

---

### Post by b@sh_n3rd on 2009-05-23
Hi...wpshooter, I've setup my Intel driver before but that thread *did* teach me something new :D...anyways, I discovered that when I use the Linux 2.6.29 Kernel, all probs stop...nothing until now...so I caught the culprit...the 2.6.30-rc6 kernel...Thanks guys :D

---

### Post by b@sh_n3rd on 2009-05-26
> I discovered that when I use the Linux 2.6.29 Kernel, all probs stop... Make that the, "2.6.28" kernel, formally supplied with Jaunty. Jaunty started loading that one automatically after I uninstalled rc6. The *29 kernel does in fact, lack the two bugs which cause other apps and X to crash, but has another bug which causes text to get garbled. The *28 kernel on the other hand, has no problem at all. Why is it better than all the others? Currently, testing the rc7...I witnessed no problems so far...

---

