---
title: "Emerald theme"
date: 2008-12-26
forum: Desktop Environments
---

### Post by eshant_engineer on 2008-12-26
every time during startup i have to run command "emerald --replace" to use the theme. please give any guidance to get  rid of this prob....:confused:

---

### Post by ELF_O8 on 2008-12-26
Go to System -> Preferences -> Sessions, and make a new session startup program using ```
 emerald --replace 
```This will load the theme every startup. Works perfectly.

---

### Post by mcduck on 2008-12-26
..or configure the correct window decorator in Compiz settings: open the CompizConfig Settings Manager, go to Effects/Window Decorations and set the command to start emerald in the "Command"-field.

---

