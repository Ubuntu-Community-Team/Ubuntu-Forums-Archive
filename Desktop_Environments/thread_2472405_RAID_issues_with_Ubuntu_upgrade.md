---
title: "RAID issues with Ubuntu upgrade"
date: 2022-02-25
forum: Desktop Environments
---

### Post by alexloz on 2022-02-25
Hi - I recently upgraded (installed a new OS, not upgrade in place) a machine from 15.04 to 21.10. This system has a large (10+) number of raid arrays, mostly using the 1.2 superblock system of having names that map the /dev/md/* to the real devices. When starting ubuntu, the raid arrays are assembled very slowly - dmesg times are [COLOR=#1D1C1D][FONT=Slack-Lato]1947.971114 then [/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]2135.912487 for instance, and every now and then it finds and assembles another one.
[/FONT][/COLOR]I have a set of tools that know how to assemble them myself (for disaster recovery) - if I just do mdadm --assembles, everything works fine and there is no delay, but I need to them assemble them manually. 

My question is - what is causing this process to be so slow in this new release - what changed that I'm unaware of? I don't even know how to begin investigating this.

---

### Post by TheFu on 2022-02-26
Wow. Just wow.

You shouldn't use 21.10. Use 20.04 and in the June 2022 timeframe consider moving to 22.04. Users who cannot or will not upgrade the OS while support is available need to only install LTS releases.  I'm in that group. 21.10 has about 4 months of support remaining. It isn't worth your time (or mine).

Non-LTS releases, like 15.xx or 21.10 are where Canonical tries new stuff and doesn't expend the same effort in solving issues.  For the most stable OS, stick to only LTS releases.  Those are all 2[02468].04 releases - even years - in April. Plan your future OS upgrades until 2030 today based on that information. Ignore releases in odd years or October.
As for the RAID stuff, I think the lack of staying on supported releases is much more important.

---

### Post by alexloz on 2022-02-26
Thanks - that's not the reply I was hoping for, as it's a big pain to install a new system on this thing. I'll give it a try and see how it goes.

Is this not something that's easily understood, then? It's bizarre, something is assembling arrays even if I stop them.

---

### Post by TheFu on 2022-02-26
It is an automatic thing, part of the boot sequence. 99.99999999999% of the world likes that. I know I do.
You can ensure they aren't mounted by using fstab options, but I've honestly never wanted them NOT to assemble at boot.  

RAID is for HA (and little else), so if the system is running, having the storage available seems mandatory. If that isn't the goal, perhaps some other storage architecture would be a better fit?

You could edit the mdadm.conf and remove the details of the existing arrays. That might work. I haven't (and won't) test it here. I need my arrays up and available all the time. Anything less is for normal storage.

---

### Post by alexloz on 2022-02-26
Changing the ubuntu version worked, it's all working a lot smoother. but the mdstat instead of listing actual devices is listing dm-### devices - maybe this should be another question, but do you know how to stop that?

---

### Post by alexloz on 2022-03-01
I'll look into it, thanks. I can understand why it's a good thing - but when you suddenly have a faulty disk that hangs the kernel when a raid array is trying to sync, it's a situation you want to have some control over! As it is now, it's basically a rush to stop the array in time until I actually have time to sit down and deal with the problem. What's new in this Ubuntu (which otherwise is wonderful, thanks again) is that after I --stop it, it re-assembles it! Is that still something about mdadm.conf? 

Thanks for all the help!

---

### Post by TheFu on 2022-03-01
Just don't mount the array device (fstab - comment that line out). Then if it gets assembled, you can stop the array easily. Of course, the OS or other critical system files cannot be stored on the array.

BTW, nobody here works for Canonical.

---

