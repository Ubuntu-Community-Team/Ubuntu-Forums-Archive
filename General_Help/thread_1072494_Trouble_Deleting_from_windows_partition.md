---
title: "Trouble Deleting from windows partition"
date: 2009-02-17
forum: General Help
---

### Post by Stan15 on 2009-02-17
I download a lot of movies and tv shows and because Xubuntu is on a small partition I normally download them to my windows partition where there's plenty of space. The problem arises when I try to delete something I downloaded, my cpu instantly hits 100% and takes about thirty seconds to delete a 200MB show then I have to stop and empty the trash. 

I'm new to linux so I'm wondering if there's an easier way to delete from my windows partition without all the hassle.

---

### Post by Slim Odds on 2009-02-17
rm in a terminal, BUT BE VERY, VERY CAREFUL

---

### Post by Therion on 2009-02-17
Would adjusting your partitions be out of the question?  

You could, if you wanted, shrink your Windows partition and give your Xubuntu partition a little more breathing room.

Just something to think about.

---

### Post by Stan15 on 2009-02-17
I already tried rm but it didn't work. I checked the man page though, most of it went over my head but it looks like I can't delete from the windows partition without a different command.

I'd like to change the partition sizes but I don't know how and it seems a bit risky as I have no place to back up my data.

---

### Post by InspiredIndividual on 2009-02-17
rm should work, I think. I checked it at my own system, and I had no problem whatsoever. Maybe the Windows partition wasn't mounted when you tried rm?

---

### Post by Stan15 on 2009-02-17
It's definitely mounted but I keep getting a no such file or directory error

---

### Post by Stan15 on 2009-02-17
I just figured this out. rm wasn't working because the files I was trying to delete all contained special characters. Sorry to waste your time but thanks for helping.

---

### Post by InspiredIndividual on 2009-02-17
> **Stan15 said:**
> I just figured this out. rm wasn't working because the files I was trying to delete all contained special characters. Sorry to waste your time but thanks for helping.

You're welcome. Good to see you managed to solve it!

---

