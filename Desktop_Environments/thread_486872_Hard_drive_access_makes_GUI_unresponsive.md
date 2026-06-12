---
title: "Hard drive access makes GUI unresponsive"
date: 2007-06-28
forum: Desktop Environments
---

### Post by monstermunch on 2007-06-28
Hi,

I'm running Feisty Kubuntu. I was recently running keep, a KDE backup utility that runs rdiff. I had it back up 10Gb of files from my main hard drive (contains home, root etc) to an empty one. This took about 30 minutes. Throughout this time, my GUI was very unresponsive. If I changed application, I would get an empty window at first and it would painfully load over 30 seconds or so. Scrolling would sometimes freeze for a few seconds too. Doing anything new, like clicking the k-menu/start-button would take ages to happen, presumably because it needed to access the hard disk.

I have a dual-core CPU and rdiff was running at about 80% on only one core. I have 2GB RAM and had loads of memory free. hdparm says DMA is turned on for each of my drives. I reniced rdiff to 19 and it didn't make any difference.

What can I do to keep my GUI responsive when the hard drive is being accessed? I don't understand why it hurts responsiveness so much, especially when hard disk access isn't required (e.g. switching to an already open app when I have memory free).

Would switching to the low latency kernel (the one for audio applications) help?

Thanks.

---

### Post by trak87 on 2007-06-28
Look at the 'nice' command. You can change a process's priority with it.

---

### Post by monstermunch on 2007-06-28
> **trak87 said:**
> Look at the 'nice' command. You can change a process's priority with it.

Thanks for the reply, but I said I reniced the process to 19 above and it didn't improve anything much.

---

### Post by warcriminal on 2007-06-28
You might be experiencing a problem with copying files that are currently in use or open.  If you are backing up absolutely everything then that is the case.  UBUNTU doesn't have your typical "root" user so if you are backing up a currently open and active account you won't get errors, but you'll get a bunch of files that cannot be copied because they are in use, these locks will slow your system down to the point of unresponsiveness without maxing out any resources.

---

### Post by monstermunch on 2007-06-28
> **warcriminal said:**
> You might be experiencing a problem with copying files that are currently in use or open.  If you are backing up absolutely everything then that is the case.  UBUNTU doesn't have your typical "root" user so if you are backing up a currently open and active account you won't get errors, but you'll get a bunch of files that cannot be copied because they are in use, these locks will slow your system down to the point of unresponsiveness without maxing out any resources.

Perhaps, but I was doing lots of different things like accessing websites with Konqueror and looking in the kmenu. For the full copy time, it was making everything slow and unresponsive, both for things that needed drive access and not. For instance, I can't see what files konqueror is going to need access to except config files, and these would take minimal time to copy so would only be locked for a tiny amount of time.

---

