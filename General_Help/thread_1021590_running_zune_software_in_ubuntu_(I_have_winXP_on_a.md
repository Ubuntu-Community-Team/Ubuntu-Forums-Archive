---
title: "running zune software in ubuntu (I have winXP on a partition)"
date: 2008-12-25
forum: General Help
---

### Post by Luksion Knight on 2008-12-25
So I heard there was a way to access windows from ubuntu even though its in a partition, how do i do this? and does it work with zune software?

---

### Post by ajcham on 2008-12-25
I'm not aware that you can use software from your Windows partition in Linux - certainly you can access the files if the disk is mounted, but that's it.

To run Windows software in Linux you can use Wine - however, this is not an option for the Zune software (according to the Wine [appdb]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741")). It is a Microsoft product after all, so it stands to reason they would make their software incompatible. Even in instances where you can use Wine you would install the software into a virtual C: drive in your Linux system, using Wine to run the setup program, rateher than running programs from your XP partition.  There may be techniques I'm not familiar with, however.

Another option is to install Windows within Linux using a Virtual Machine - you can search the forums for more info on this.

---

### Post by Luksion Knight on 2008-12-26
well is there some way i can get ubuntu to ignore the zune when i plug it in so that i can at least charge the thing while running ubuntu (i have no AC adaptor)

---

### Post by DucksAndDolphins on 2008-12-26
> **Luksion Knight said:**
> well is there some way i can get ubuntu to ignore the zune when i plug it in so that i can at least charge the thing while running ubuntu (i have no AC adaptor)

just plug it in with the chord they give you; it doesnt matter if its installed or not. i even did it with my brothers ipod, it just charges. 

i am searching for the answer to your problem as well; the only way to run windows is through VMware. The Zune software is one of the only things you cannot download or run through Wine, which means you need a Virtual Machine (VM) to run it. VMware is proving hard to get; keep me updated if you find anything.

---

### Post by Frak on 2008-12-26
> **Luksion Knight said:**
> well is there some way i can get ubuntu to ignore the zune when i plug it in so that i can at least charge the thing while running ubuntu (i have no AC adaptor)
Just plug it in.

Oh, and the only reason Zune's don't work under Linux right now is solely because Microsoft implemented a secret handshake that only very few, if any, people know how to crack right now. Amarok is the closest and all it can do is delete songs.

---

