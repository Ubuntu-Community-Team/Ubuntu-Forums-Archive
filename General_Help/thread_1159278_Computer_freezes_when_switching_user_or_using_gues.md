---
title: "Computer freezes when switching user or using guest session"
date: 2009-05-14
forum: General Help
---

### Post by paopao on 2009-05-14
I am running Ubuntu 8.10 on a Sony VAIO VGN-FW390.  I have two accounts.

When I sign into one of the accounts, I various options in the upper-right hand corner regarding switching user, shutting down, logging off, etc.  If I try to switch to the other user or use a guest session while still logged in as the first account the computer will lock up, freeze and I have to manually shutdown with the power button.

Has anyone else have any similar problems and found any solutions?  Thanks!

---

### Post by drs305 on 2009-05-14
To try to isolate the problem, you might try creating a third user with completely default settings (System, Administration, Users & Groups). Once you have that user created, try switching to the new user (#3) and see if you have the same problem. If you don't, the trouble probalby lies in one of the configuration files of user #2's $HOME.

---

### Post by paopao on 2009-05-14
I made a new account, with default settings.  I tried going from account 1 to this new account, new account back to account 1, new account to guest account and account 2 to new account.  All of these resulted in freezing the computer.  The process was like this: First, the screen flickers and shows a bunch of colors, similar to the TV color bars.  Then the screen turns off, then it turns black (since it's an LCD screen, it's more like a dark grey).  Then it just sits there for a long time (well, I've only waited several minutes before just shutting it off).  I cannot do anything, ctrl+alt+F-keys don't work.  If anyone can offer any help ...

---

