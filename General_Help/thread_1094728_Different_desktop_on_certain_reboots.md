---
title: "Different desktop on certain reboots?"
date: 2009-03-12
forum: General Help
---

### Post by kennedyjch on 2009-03-12
Under 8.10 when my PC reboots and I log in I at times get a desktop without the various files that I have stored on the desktop. If I reboot and re-login, I will invariably get the "familiar desktop" with all the various icons and files.

I've also noticed that the remembered passwords for certain websites are different...

Anyone able to point me in the right direction to resolve this mystery?

Not so much of a problem for me, but very difficult to explain to family members that if the desktop is different, to reboot and try again...

---

### Post by hockeyhead019 on 2009-03-12
maybe a different user name? or password or something? are you sure you're putting in the same password and everything as you (or somebody else in the family) may have accidentelly created an account with the same user name and a password one letter or so different from your own... i dunno if that's it just and idea haha

but can you still access the same "Home" folder?

---

### Post by Defrector on 2009-03-12
Sounds like user/home directory wackiness.


In each scenario, type "whoami" in the terminal, hit ENTER and see what comes up. If they're different then somehow you're logging in as different identities.

---

### Post by kennedyjch on 2009-03-14
Thanks for the responses. Indeed logging on with the same username and same password. It seems that alternate reboots I get a different desktop (i.e., one time a "clean" desktop (i.e., old one); the other times the real one with all sorts of files that I've placed there). 

I'll try the whoami and report back.

---

### Post by kennedyjch on 2009-11-13
Update and conclusion: I made a copy of my active partition as backup on one of the alternate partitions on my PC. It appears that from time to time Grub decides to boot from the old one.

Appears that this problem has been fixed with updates since my original post.

---

