---
title: "get status of long &quot;cp&quot; procedure"
date: 2008-12-24
forum: General Help
---

### Post by jimmy the saint on 2008-12-24
I am copying a large directory (110Gigs) from my server to a usb drive that is attached to it.  It has been running a long time.  i would like to get the status of the command, or at least confirmation that it is still working.  How would I go about doing this?  I am connected to the server via ssh from my laptop.

---

### Post by Xiong Chiamiov on 2008-12-24
If it hasn't finished yet, then it's still going.

AFAIK, there isn't much you can do after you've already started it (aside from looking at the processes in (h)top), but **before** you start copying, you can use -v to get notification when individual files get done, or use [one of the many]("http://www.linuxquestions.org/questions/linux-general-1/cp-progress-bar-407381/") "cp with progress bar" scripts floating around (#11 appears to be the best).

---

### Post by Tim Sharitt on 2008-12-24
I'm not sure how to tell where you are as far the copying progress is concerned, but 'ps' could tell you if its still running. You may have to use 'ps a' if you didn't start the copying from you current session.

---

### Post by hyper_ch on 2008-12-24
does cp not have a -v switch for verbose?

---

### Post by vanadium on 2008-12-24
That is what Xiong Chiamiov mentioned among other options.

---

### Post by jimmy the saint on 2008-12-24
Thanks guys.  It finished shortly after I asked.  I will definitely use -v next time.  It took over an hour and I got a little concerned!  Also, I was SSHed into the machine and I have never needed multiple ssh sessions, so I had never tried.  I really didn't feel like trying it out in the middle of a long process like that one.

---

### Post by vanadium on 2008-12-25
A little tip for you: get to know the "screen" program. With "screen", you can give your copy command, detach the session and logout while the session continues on the host, and come back later to see how it went.

---

