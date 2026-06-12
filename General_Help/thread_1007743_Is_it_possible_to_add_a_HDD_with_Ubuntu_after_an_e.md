---
title: "Is it possible to add a HDD with Ubuntu after an existing XP install?"
date: 2008-12-10
forum: General Help
---

### Post by Roasted on 2008-12-10
Say I have a computer... 1 IDE hard drive... XP Pro.

Then I add another IDE hard drive... 

Can I install Ubuntu on that 2nd hard drive without any issues? I'm trying to set it up on my spare rig and it's not working the way I wanted... but this computer has so many problems I'm not sure if it's an issue with the installs between 2 drives or not.

---

### Post by haggus on 2008-12-16
> **Roasted said:**
> Say I have a computer... 1 IDE hard drive... XP Pro.

Then I add another IDE hard drive... 

Can I install Ubuntu on that 2nd hard drive without any issues? I'm trying to set it up on my spare rig and it's not working the way I wanted... but this computer has so many problems I'm not sure if it's an issue with the installs between 2 drives or not.

It will work just make sure when your partitioning you select hdb and use entire disk. Your ubuntu install will go to hdb and grub will update so you will see xp in the list at startup.

---

