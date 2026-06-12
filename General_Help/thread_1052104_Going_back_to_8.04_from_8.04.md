---
title: "Going back to 8.04 from 8.04"
date: 2009-01-27
forum: General Help
---

### Post by Ouoertheo on 2009-01-27
Hello,
I just recently upgraded to UbuntuStudio 8.10 from 8.04, but realized that it doesn't support dual core processors. How do I go back to 8.04 or maybe go back to an rt kernel that does support dual core processors?

---

### Post by snowpine on 2009-01-27
Hi there, sorry to say Ubuntu does not have a "downgrade" feature--you would need to re-install 8.04 if that's the route you choose. I hope you can find an alternate solution. :)

---

### Post by wolfen69 on 2009-01-27
> **Ouoertheo said:**
> Hello,
I just recently upgraded to UbuntuStudio 8.10 from 8.04, but realized that it doesn't support dual core processors. How do I go back to 8.04 or maybe go back to an rt kernel that does support dual core processors?

i have used ubuntustudio and can say that it does support dual core processors. every major distro has for some time. you can choose to do a clean install of ubuntustudio 8.10 and it *will* support both processors. up to you.

---

### Post by jespdj on 2009-01-27
> **Ouoertheo said:**
> Hello,
I just recently upgraded to UbuntuStudio 8.10 from 8.04, but realized that it doesn't support dual core processors.
What do you mean? Where did you get that information from? 8.04 as well as 8.10 (Studio and the normal version) do support dual-core processors, and you do not need any special kernel for that. Why do you think it does not support dual-core processors?

---

### Post by Ouoertheo on 2009-01-27
Lol, just noticed i messed up the title!

But anyways, maybe I'm getting confused, it says here - [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) - that smp is not supported in the new ubuntustudio 8.10... I assumed smp was the support for multiple processors/cores, I'm guessing from the reactions that that is not true.

I just noticed that only one cpu is showing up after my upgrade, not to mention it does not run very smooth.

Is it probably something mis-configured that would cause only one cpu to be recognized?

P.S. Is there a way I can fix the title of the thread?

---

### Post by Ouoertheo on 2009-01-27
Some more info:
you@rockathon:~$ dmesg | grep CPU
[    0.000000] WARNING: NR_CPUS limit of 1 reached. Processor ignored.
[    0.000000] Initializing CPU#0
[    0.000999] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000999] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.000999] CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03

---

### Post by jespdj on 2009-01-28
From the release notes:
> **UbuntuStudio real-time kernel support**

The real-time kernel variant included in Ubuntu 8.10 does not include SMP support. Users of UbuntuStudio 8.04 who need real-time kernel support for dual-core, dual-processor, or more complex SMP configurations are advised not to upgrade to UbuntuStudio 8.10 at this time.
Well, it looks like you were right. The real-time kernel for UbuntuStudio 8.10 indeed doesn't support multi-core processors. :( However, it's the RT kernel that does **not** support SMP, so "go back to an rt kernel" as you suggested in your opening post won't work.

And the text from your dmesg indeed indicates that it's using not more than one CPU core.

Unfortunately, there is not an easy way to downgrade from a newer to an older version of Ubuntu, as far as I know. You'd have to reinstall version 8.04.

---

### Post by Ouoertheo on 2009-01-28
Damn... well thanks for the replies. I guess I'll be awaiting that feature.

---

