---
title: "How do I identify disk access?"
date: 2009-04-27
forum: General Help
---

### Post by blippy on 2009-04-27
I had Slackware going a few weeks ago, and it was quite quiet. Now that I have installed Jaunty, I have noticed the disk clicking away. I wonder if I can identify the process that is causing the disk access.

If I type 
free -m
I get
             total       used       free     shared    buffers     cached
Mem:           987        938         49          0         75        535
-/+ buffers/cache:        327        660
Swap:         2929          0       2929

So assume that the disk access I am hearing is not due memory swapping. I am not opening or closing any programs at the moment, so I presume that there's something going on in the background that is causing all the disk access.

---

### Post by rajeev1204 on 2009-04-27
> **blippy said:**
> I had Slackware going a few weeks ago, and it was quite quiet. Now that I have installed Jaunty, I have noticed the disk clicking away. I wonder if I can identify the process that is causing the disk access.

If I type 
free -m
I get
             total       used       free     shared    buffers     cached
Mem:           987        938         49          0         75        535
-/+ buffers/cache:        327        660
Swap:         2929          0       2929

So assume that the disk access I am hearing is not due memory swapping. I am not opening or closing any programs at the moment, so I presume that there's something going on in the background that is causing all the disk access.

Install htop from synaptic may give you an idea.

---

