---
title: "Packages."
date: 2009-02-04
forum: General Help
---

### Post by Chase Young on 2009-02-04
Hey, I just downloaded Ubuntu this morning, burned it to the disc, all that fun stuff, now I'm just playing on it and whatever, and I'm trying to add programs with the add/remove programs button (applications>add/remove..) But every time I try to add a program, let's use Eclipse as an example, it gives me the "Unable to get an exclusive look" error, then I can't install it. I'm no fool, I'm not using the terminal *at all* for *anything,* much less a package management command, yet I still get this error. I logged off once just to make sure I wasn't running anything I couldn't see, but I'm still getting the error. Does anybody know how to fix this?

Thanks a lot guys, in advance,

Chase.

---

### Post by Sidewinder1 on 2009-02-04
You can not add or remove programs if you're running in "live cd", as it's all in ram. You must "install" ubuntu first. In order to do that you must repartition your drive (assuming you currently have a windose box), and then install ubuntu to the ext3 partition that you created. Before any repartitioning, remember to defrag the NTFS/Fat32 (from within windose) partition first.
Hope this helps.

---

### Post by Chase Young on 2009-02-04
I did install it, sorry if that came across wrong.

---

### Post by Sidewinder1 on 2009-02-04
Sorry I misunderstood you :-)
I found this in another thread which may be related to your problem:
"Unable to get exclusive lock"

"This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first."

Could that possibly be the case?

---

### Post by mb_webguy on 2009-02-04
You generally get this error if you try to run two application managers (such as Update Manager, Add/Remove Applications, or Synaptic) at once.

EDIT:  Sidewinder beat me to it.

---

### Post by Chase Young on 2009-02-04
I know that, but as I stated in the topic starter, there's nothing else even open. Nothing else is downloading.

---

### Post by mb_webguy on 2009-02-04
Hrm.  I hate to suggest this (since it's rarely the answer for Linux like it tends to be for Windows), but have you tried rebooting?

---

### Post by Chase Young on 2009-02-04
Umm..I didn't, but I hate to say I wasted your time. It seems I had a download going on in my tmp folder and it was closed so I forgot about it...

I'm really sorry guys, I've wasted your time.

---

### Post by Sidewinder1 on 2009-02-06
No problem. :-) If you haven't already done so, please mark thread as solved.
Thanx,
Side

---

### Post by mb_webguy on 2009-02-06
Actually, Sidewinder1, he can't -- the Solved and Thanks functions aren't currently available.

---

