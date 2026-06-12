---
title: "How do I diagnose system locking up?"
date: 2021-08-15
forum: Desktop Environments
---

### Post by veloce on 2021-08-15
I have a recurring problem with one of my Ubuntu machines.  When left running, it will sometimes freeze. Everything stops and it is completely unresponsive.

I've searched and all I can find is comments about it most likely being memory problems but how do you tell?  

Shouldn't there be something in some log somewhere? Or is there some  monitoring software that I could install?

Because it happens when I've left it idle it's very difficult to work out what is going on.

Is there a process to follow?

Thanks!
Kerry

---

### Post by TheFu on 2021-08-15
Look at the system logs.  **journalctl** can do filtering by timestamp ranges, so if you know when the lockup happened, you can get to the minutes before it and check the logs easily.  Look for errors and warnings.  Feed those into google. Find solutions or others with the same issue.  A stack trace  may seem like junk, but the names at each level can provide a clear idea for the cause.

And trying an older kernel which doesn't show the issue can be helpful.  If the exact kernel release where it worked fine, but the next kernel broke it can be found, there's a much greater chance for a fix.  

Being able to reproduce the issue will be key in any fix. If a kernel developer can reproduce the issue, then a fix can happen in days.  If they cannot reproduce the issue - forgetaboutit.

---

### Post by guiverc on 2021-08-15
If it was me, I'd do the following (*note: I don't know your OS & release, whether desktop or server, so this won't be as precise as it may have been if I'd known*).

- can i switch to text terminal & login to explore?
- can i login from remotely (ie. `ssh` in? *assuming the box is enabled for this*)
- is the kernel up & running normally, ie. kernel responds to SysRq commands still? as a stuck/frozen GUI can be safely killed; file-systems sync'd & unmounted etc

If the SysRq keys didn't get a response; I'd start thinking *hardware* personally.  I'd likely open the box & do a *cap scan* of the motherboard & components (ie. *looking for swollen capacitors or signs of hardware issues*) before I ran the RAM test esp. if SysRq failed to do anything - ie. a kernel panic with no messages on screen make my think of hardware.

I'd likely run RAM tests at minimum overnight, but if I wanted to trust the machine more likely two-three days (*if it locks up doing this simple well-tested code; it's almost guaranteed to be hardware or firmware settings that are an issue; not your OS; though note, some boxes don't like some of the RAM testing software so I've had boxes where I don't use this testing*)

---

