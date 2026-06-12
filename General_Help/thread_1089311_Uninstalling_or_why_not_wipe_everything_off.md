---
title: "Uninstalling or why not wipe everything off"
date: 2009-03-07
forum: General Help
---

### Post by limiz on 2009-03-07
I like one or the other..I have my system recovery disc for my xp.. So I don't care if I wipe everything off my Computer. Why?? My fist Linux was Open SuSe. It ok. But install it wrong. And why I did my system recovery disc. It never really uninstall my linux. Weird right? But I did not find that out tell I install ubuntu. and find stuff still form SuSe. I was thinking... I how do I wipe out everything off my computer.. all of it. Ubuntu, SuSe, and XP!!!

Can you guys help me with this??

---

### Post by adult swim on 2009-03-07
boot your ubuntu live cd, then go to a terminal and enter in ```
gksudo gparted
```  when the window comes up, delete all of the partitions and click apply.

---

### Post by limiz on 2009-03-07
> **adult swim said:**
> boot your ubuntu live cd, then go to a terminal and enter in ```
gksudo gparted
```  when the window comes up, delete all of the partitions and click apply.

This may sound noobie but whatever... How would I know what is a partitions or not?? Are they all partitions?

---

### Post by adult swim on 2009-03-07
it will show only partitions, so if you delete all of them, your drive will be empty

---

### Post by limiz on 2009-03-07
Thank you. Your the only that answered my question.:P

---

### Post by sdennie on 2009-03-07
Using gparted will erase the partition table but, all the data is still there.  In fact, if you know what the old partition table was, you can restore all your data just by recreating the partition table.  In this case, just erasing the partition table is probably sufficient but, you should just bear in mind that in the future, deleting partitions doesn't delete data and it's not difficult to get that data back.

---

### Post by adult swim on 2009-03-07
i was going to point this out but i didnt think it was warranted in this situation.  i think he just wanted to make sure that he was claiming all of his disk space.

---

### Post by sdennie on 2009-03-07
> **adult swim said:**
> i was going to point this out but i didnt think it was warranted in this situation.  i think he just wanted to make sure that he was claiming all of his disk space.

Right.  Removing the partitions should be all that is needed in this case.  I just wanted to make sure no one stumbling on this would confuse, "remove partition table" with "wipe".  ;)

---

### Post by adult swim on 2009-03-07
i always forget these things are archived! :)

---

