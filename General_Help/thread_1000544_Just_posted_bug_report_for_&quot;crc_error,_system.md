---
title: "Just posted bug report for &quot;crc error, system halted&quot;..."
date: 2008-12-03
forum: General Help
---

### Post by Jammanuser on 2008-12-03
Well...i've just made a bug report on the "crc error, system halted" boot problem! hopefully someone comes up with a fix...

in case anyone wants to view it, it can be found here: 
[https://bugs.launchpad.net/wubi/+bug/304665](https://bugs.launchpad.net/wubi/+bug/304665)

let me know if i should change anything in the report, or add more details! lol

-jammanuser

:D

---

### Post by magmon on 2008-12-03
Good, now maybe the posts related to this bug will die! lol, it seems really common. Ya got my prayers for a fix!

---

### Post by Jammanuser on 2008-12-03
> **magmon said:**
> Good, now maybe the posts related to this bug will die! lol, it seems really common. Ya got my prayers for a fix!

well...i hope they don't die!!! at least until **someone** comes up with a fix for it...it'll help motivate the bug-fixers to work on it, the more common the bug is! so i hope people keep mentioning it on the forums, and wherever else...so that someone does! xD 

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-03
ANYONE else have anything to add?

Feel free! ;)

Cheers! :D

-jammanuser

---

### Post by rewolff on 2008-12-14
The standard answer that pops up EVERYWHERE when you google for this problem is that people are suggesting that the hardware is broken. Usually people suggest the harddrive, however that would give different error messages. Moreover, I don't have a harddrive in that machine, so it can't be broken. I'm pretty sure of that. 

In theory it could be that RAM is broken, and dropping bits. However, I'm able to boot a linux-2.4 kernel just fine. Why would my RAM be broken if linux-2.4 runs fine?


My system is quite old. I have 32M of ram.

---

### Post by Jammanuser on 2008-12-14
> **rewolff said:**
> The standard answer that pops up EVERYWHERE when you google for this problem is that people are suggesting that the hardware is broken. Usually people suggest the harddrive, however that would give different error messages. Moreover, I don't have a harddrive in that machine, so it can't be broken. I'm pretty sure of that. 

In theory it could be that RAM is broken, and dropping bits. However, I'm able to boot a linux-2.4 kernel just fine. Why would my RAM be broken if linux-2.4 runs fine?


My system is quite old. I have 32M of ram.

hmm...r u **also** having the "crc error, system halted" error message at bootup? :D in my case it **wasn't** the hardware, and the only fix that i found for it was to simply reinstall Wubi, keeping the old root.disk, and then later replacing the new after finishing the reinstall! This allowed me to recover all my files and programs that i had installed on my OLD installation of Wubi, before the crc error...

Hope it works for u too! ;)

Cheers! ):P

Jam Man

:guitar:

---

### Post by brandon88tube on 2008-12-15
Are you sure this a Wubi error? It seems to me that this might just be a Debian error in general as it popped up in 2005 on this thread [http://ubuntuforums.org/showthread.php?t=71772](http://ubuntuforums.org/showthread.php?t=71772)

---

### Post by Jammanuser on 2008-12-15
> **brandon88tube said:**
> Are you sure this a Wubi error? It seems to me that this might just be a Debian error in general as it popped up in 2005 on this thread [http://ubuntuforums.org/showthread.php?t=71772](http://ubuntuforums.org/showthread.php?t=71772)

hmm...those ones u directed me to r not the same as my own problem that i had! ;) in the actual page u linked me to, the "crc error" that they had was not a booting problem...it sounded like it was a problem with the CD-ROM! i also clicked on the link on that webpage which sent me to the debian forums, where someone had posted a crc error...that ALSO was a little bit different! ;) It seems the problem in that case WAS hardware related...while mine was not! :D Mine was **indeed** a Wubi error...

Anyway, like i mentioned above, i'm past the crc error now...i got around it by simply reinstalling Wubi, and keeping the old root.disk which i then used to replace the new one after the reinstall! :guitar:

Of course it WOULD be nice (just for knowledge's sake, if such a thing was to happen again to me, and also for the many people that may encounter the same crc error) if someone would come up with a REAL fix to the problem...instead of just reinstalling Wubi! :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

