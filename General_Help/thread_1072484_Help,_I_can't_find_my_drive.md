---
title: "Help, I can't find my drive"
date: 2009-02-17
forum: General Help
---

### Post by Jedit Ojanen on 2009-02-17
Hello.

I installed Ubuntu about a month ago and everything worked fine until now. Suddenly I can't open my drive. A window pops up telling: "Cannot mount volume". I haven't done any changes in the system. I have Windows installed also but I don't remember changing settings there either.

I have the latest version of Ubuntu.

---

### Post by InspiredIndividual on 2009-02-17
Do you mean your cd/dvd-drive?

---

### Post by Jedit Ojanen on 2009-02-17
> Do you mean your cd/dvd-drive?

No, hard drive. I can actually find it but I can't open it. I just can open the drive where Ubuntu is installed.

---

### Post by taurus on 2009-02-17
Have you mounted it?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by InspiredIndividual on 2009-02-17
I suppose you mean you can't access your Windows files from Ubuntu? I had the same problem some time ago. In my case, it was caused by a bad Windows shutdown. If you've got the Partition editor installed (System > Administration > Partition Editor) you can check quickly whether your problem is similar to mine. In my case, there was a warning  triangle next to the Windows partition. If you haven't, you could access the Partition Editor from a LiveCD. But as that requires a restart as well, I'd just boot into Windows and restart. That solved the problem for me.

---

### Post by Jedit Ojanen on 2009-02-17
> I suppose you mean you can't access your Windows files from Ubuntu? I had the same problem some time ago. In my case, it was caused by a bad Windows shutdown.

Yes, that was the case. I just restarted to Windows and restarted back to Ubuntu and it worked again. Thanks for the help :).

---

### Post by partsdale on 2009-02-17
so this is "solved"?  - - making a subliminal suggestion as he asks...

---

### Post by InspiredIndividual on 2009-02-17
> **partsdale said:**
> so this is "solved"?  - - making a subliminal suggestion as he asks...

If you mean the thread should be marked as 'solved', this option is currently not available anymore.

---

### Post by partsdale on 2009-02-17
> **InspiredIndividual said:**
> If you mean the thread should be marked as 'solved', this option is currently not available anymore.

That's too bad... I thought it was very helpful.

---

