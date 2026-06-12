---
title: "X broken after firewall changes"
date: 2023-01-16
forum: Desktop Environments
---

### Post by johntelek on 2023-01-16
I disabled firewalld because I could not accept inbound connections for some reason my X login broke.
The machine boots and comes up with a black screen and a dialogue box asking for the password to unlock
the key-chain which disappears after  I hit unlock and then nothing.

And why is it I cannot goto ubuntuforums.org from firefox in Debian 11. It's seems to be blocked but the main Ubuntu.com site is accessible.
The same with Konqeror. I am writing this from a windows VM on my Debian machine to get around the problem.

Help please

   John

---

### Post by deadflowr on 2023-01-16
Debian? Firewalld?
We need more information about what is what and how any of this relates to Ubuntu.

---

### Post by johntelek on 2023-01-18
It's ok I fixrd it. I'm running Ubuntu 22.04 and was unknowingly running both firewald and ufw. Disabling UFW fixed my broken X issue.

cheers
    John

---

### Post by mIk3_08 on 2023-01-18
> **johntelek said:**
> It's ok I fixrd it. I'm running Ubuntu 22.04 and was unknowingly running both firewald and ufw. Disabling UFW fixed my broken X issue.

cheers
    John
Wow!... cool. firewald authored by (Thomas Woerner) from redhat. you can also use it to Debian GNU/Linux Desktop. And now its already running smoothly into Ubuntu 22.04 LTS (Long Term Support) Operating System.  Good Luck. Regards and cheers.

---

### Post by mIk3_08 on 2023-01-18
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

