---
title: "Reset Nautilus Settings"
date: 2008-08-03
forum: Desktop Environments
---

### Post by lusiads on 2008-08-03
Some features on Nautilus are not functional on my account, on other accounts or at root's privilege they work fine.

I'm trying to find a way to reset Nautilus settings.

I can find no references to this sort of problem on google. Does anybody have any ideas? :confused:

---

### Post by sayakb on 2008-08-03
At a terminal:
```
mv ~/.nautilus ~/.nautilus_old
```
And then restart X (Ctrl+Alt+Backspace)

---

### Post by lusiads on 2008-08-03
What's about .gconf*?
Does it affect the way Nautilus works.

Thank you for your hard work,

---

### Post by sayakb on 2008-08-03
.gconf is not associated with nautilus only but all applications which have environment variables. Do not make any changes to that folder.

---

### Post by lusiads on 2008-08-03
I tried to rename ~/.nautilus but that does not solve nautilus issues, for example, typing-to-select feature is (do you know the name of this feature?) still not functional.

---

### Post by sayakb on 2008-08-03
Try reinstalling nautilus:
Press Ctrl+Alt+F1 and login. Then type in:
```
sudo apt-get purge nautilus
sudo apt-get install nautilus* nautilus-cd-burner* nautilus-sendto* nautilus-share
```

---

### Post by lusiads on 2008-08-03
I tried to remove and reinstall nautilus by following your intructions but the problem still persists.
Keep in mind that on other accounts or at root's privilege Nautilus work just fine.

---

