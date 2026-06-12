---
title: "Dual NICs/resolv.conf/nameservers"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Rick Myers on 2006-06-06
After a clean-fresh installation of Ubuntu both Breezy and Dapper I experienced problems setting the nameservers (DNS) for just one of my NIC cards. Seems everytime I reboot the computer the nameserver entries disappear. Apparently resolv.conf is recreated during the boot process. After a couple of hours of searching and attempting several fixes, the only one I could get to work was manually entering the nameservers in resolv.conf then changing the attribute of with 'sudo chattr +i /etc/resolv.conf'.

Is this the best solution? Or can someone offer a better one?


Rick

---

### Post by detour on 2006-06-06
I was experiencing the same issue, see my thread (with solution) here: [http://www.ubuntuforums.org/showthread.php?t=181697](http://www.ubuntuforums.org/showthread.php?t=181697)

---

### Post by Rick Myers on 2006-06-06
[QUOTE=detour]I was experiencing the same issue, see my thread (with solution) here: [http://www.ubuntuforums.org/showthread.php?t=181697](http://www.ubuntuforums.org/showthread.php?t=181697)[/QUOTE]

Thanks, I read that thread before I posted. Tried it. No joy. More specifically, it had no effect on the resolv.conf file.

---

### Post by kepreon on 2006-06-09
[QUOTE=detour]I was experiencing the same issue, see my thread (with solution) here: [http://www.ubuntuforums.org/showthread.php?t=181697](http://www.ubuntuforums.org/showthread.php?t=181697)[/QUOTE]

I have the same problem -- except I only use one of the two network cards that are in my system.  It's statically configured, but still loses the nameservers on each boot.  I tried the fix, but it didn't work either.  This is after a clean install of Dapper; I had Breezy before, but experienced no such problem.  Should a bug be filed?

---

### Post by kepreon on 2006-06-10
Confirmed on a totally different machine with dual NICs and Xubuntu.

---

