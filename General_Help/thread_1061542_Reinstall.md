---
title: "Reinstall"
date: 2009-02-05
forum: General Help
---

### Post by tbrooke on 2009-02-05
I have been running Ubuntu gutsy for about a year without problem. Suddenly, after a few changes it has slowed to a crawl especially with I load applications and I can't reach the internet. The Internet connection and disk seems ok since everything is great whenI load the live CD. I have racked my brain and I can't figure out what is wrong or even where to begin to fix it. I have about 200 GIGs of music on this computer I don't want to loose. 

Is there away to simple reinstall the system file without loosing my data?

I think this might be the easiest solution. 

Tom

---

### Post by pytheas22 on 2009-02-05
If you have your /home directory on a separate partition, then you can reinstall quite easily without losing any personal files or settings.  But the default installation of Ubuntu doesn't give /home its own partition; you would have had to set that up manually (there are instructions [here]("http://www.psychocats.net/ubuntu/separatehome") for future reference).  If you don't know whether /home is on a dedicated partition, please open a terminal, run this command and post the output:

```
df -h
```

If /home is not on its own partition, your only real option would be to back up your music to an external hard drive, CD or DVD, then reinstall Ubuntu.  Shrinking your existing partition and installing Ubuntu in the empty space, then deleting the old partition and expanding the new one would also be an option, but this is risky--I wouldn't do it without backing up your data first--and would be a lot of work.

There may also be a simple solution for fixing your existing system.  Could you describe the problem in more detail?  Could you post the output of this command:
```

dmesg
```

---

