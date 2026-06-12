---
title: "System is hanging frequently after installing 12.04"
date: 2013-02-18
forum: Desktop Environments
---

### Post by rajnikhil on 2013-02-18
I have Ubuntu 12.04 running on my laptop as well as desktop. There are no issues on my laptop, although it does hang momentarily when the load increases but becomes responsive soon enough. However my desktop hangs and never becomes responsive again. The only way is to force restart it. I've observed it happen mostly when I'm streaming videos. It may freeze even when I use other load heavy programs like GIMP. When I was running 10.04 on Desktop, it often used to restart automatically when I ran such heavy programs for quite sometime and I thought the system is overheating and I need to install an extra cooling fan but now after upgrading to 12.04 it only hangs and that too just after starting the system for only a few minutes. This, to me, indicates that the issue is not with heat dissipation.

My Desktop config is:
AMD Athlon 64 2 cores,
3gb in 2DIMM ddr2, 1 chip is 1GB Ram and other is 2GB RAM. However both these chips have different frequencies.

I've tried the following two steps

1. /usr/lib/nux/unity_support_test -p
All the parameters indicate 'Yes' here.

2. Use bleachbit

but neither resolve the issue. Could someone please advice me how detect the issue and resolve it. It is really annoying when the system hangs so frequently and I'm having to avoid necessary but load heavy programs for this reason.

Thanks in advance.

---

### Post by Pandanus on 2013-02-18
Hello rajnikhil,

what do you exactly mean with system hangs? Do the windows freeze, but the cursor can still be moved? And also what kind of graphics card/graphics drivers are you using?

regards
Pandanus

---

### Post by 2F4U on 2013-02-18
Did you look into the system log files after such an event? The log files may contain a hint on what the problem is. The log files are easily accessible through an application named Log File Viewer.

---

### Post by rajnikhil on 2013-02-22
@Pandanus: Majority of the times windows' freeze but I'm able to move the cursor. I'm not sure about graphics card (I don't think I have a separate graphics card) how do I find out the details. 

@2F4U: I'm travelling right now but once I can access I'll post details once it happens and then you can help me out.

---

### Post by rajnikhil on 2013-02-26
> **2F4U said:**
> Did you look into the system log files after such an event? The log files may contain a hint on what the problem is. The log files are easily accessible through an application named Log File Viewer.

Hi 2F4U, following are the two errors when looked at the logs after the system hanged again. Could you please take a look.

Feb 27 09:27:38 raj-desktop kernel: [   21.252265] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Feb 27 09:27:44 raj-desktop kernel: [   26.784023] hda-intel: Codec #0 probe error; disabling it...

---

