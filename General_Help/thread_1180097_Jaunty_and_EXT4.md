---
title: "Jaunty and EXT4"
date: 2009-06-06
forum: General Help
---

### Post by oxf on 2009-06-06
I shortly going to be doing a clean install of 9-04. Should I install as EXT3 or 4? Is there any reason I should ---NOT---- format as EXT4?

Thanks

---

### Post by Legace on 2009-06-06
I've had absolutely no trouble so far with EXT4 :)

Some people have had, though. If you don't do anything important on your PC or if you do frequent backups or if you store your data on a separate non-EXT4 partition, EXT4 is the way to go :)

---

### Post by pauna on 2009-06-06
> **oxf said:**
> I shortly going to be doing a clean install of 9-04. Should I install as EXT3 or 4? Is there any reason I should ---NOT---- format as EXT4?


See [http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719) for longer discussion.

To recap: ext4 has some issues, but they may not bite you.

My 9.04 laptop has / using ext4 and /home ext3. The logic being that if ext4 gets hosed, I can easily do a complete reinstall without touching my data in the home directory. So far no problems.

---

### Post by oxf on 2009-06-06
> **pauna said:**
> See [http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719) for longer discussion.

To recap: ext4 has some issues, but they may not bite you.

My 9.04 laptop has / using ext4 and /home ext3. The logic being that if ext4 gets hosed, I can easily do a complete reinstall without touching my data in the home directory. So far no problems.

Thanks thats what I wanted!

---

