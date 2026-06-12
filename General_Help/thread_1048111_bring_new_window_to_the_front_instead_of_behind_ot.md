---
title: "bring new window to the front instead of behind other windows..."
date: 2009-01-23
forum: General Help
---

### Post by robriz86 on 2009-01-23
Im new with Ubuntu but... the problem I have is: if I have a folder open and I open firefox, the firefox window is opened behind the folder window, so I have to click on the firefox window to bring it to the front. can this be changed so that when i open a new program, it pops-up in front of all other windows?

thank you...

---

### Post by gettinoriginal on 2009-01-23
This sounds like a compiz settings problem.  The best suggestion is to set it all back to default and then as you change settings, try to find which one does this.  Here is the code for setting compiz back to default, in terminal copy/paste the following:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by robriz86 on 2009-01-23
thank you very much....

---

### Post by gettinoriginal on 2009-01-23
Glad it fixed it.  :p

---

