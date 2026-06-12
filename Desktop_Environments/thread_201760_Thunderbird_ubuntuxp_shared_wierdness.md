---
title: "Thunderbird ubuntu/xp shared wierdness"
date: 2006-06-22
forum: Desktop Environments
---

### Post by bohboh on 2006-06-22
I have TB shared between ubuntu and xp (not at the same time, dual boot)

When i get new emails, i have to click on each folder to see which emails i have received. If new emails exist in the folder, it turns bold after i click on it.

This isnt normal behaviour. Has anyone else had/seen this problem?

---

### Post by jvl on 2006-06-22
If you happen to use imap, add following line to your prefs.js:

user_pref("mail.check_all_imap_folders_for_new", true);

---

### Post by bohboh on 2006-06-22
[QUOTE=jvl]If you happen to use imap, add following line to your prefs.js:

user_pref("mail.check_all_imap_folders_for_new", true);[/QUOTE]

Sorry, should have said. Only use pop, not imap.

---

