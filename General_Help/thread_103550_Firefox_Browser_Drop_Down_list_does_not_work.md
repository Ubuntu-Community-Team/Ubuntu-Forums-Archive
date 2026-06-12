---
title: "Firefox Browser Drop Down list does not work"
date: 2005-12-14
forum: General Help
---

### Post by spier on 2005-12-14
In Firefox/1.0.7 (Ubuntu package 1.0.7),  when I click on the address field's URL Drop Down List button, nothing happens, not even an empty list drops. I tried everything in Edit > Preferences with no avail.  In other hand, the history (Ctrl+H) is working!

Does someone have any clues about what is happen?

Thanks in advance.

Regards, spier.

---

### Post by aysiu on 2005-12-14
So when you press Control-H, you get just empty history?
Does this still happen after you type this? ```
mv ~/.mozilla ~/.mozilla_backup
firefox
``` P.S. That command makes a backup of your old Firefox profile and creates a new one.

---

### Post by spier on 2005-12-14
Ctrl+H was working, retrieving last 9 surfing days. Just the drop down was broken, annoying since without auto completion from the list I had to type all urls everytime.

But your tip fixed the problem, everything is working again!

 Thanks! =D>

---

### Post by ronmarley1 on 2005-12-15
I see you've solved the problem.  However, you may want to try Firefox 1.5.  It smokes!

---

### Post by spier on 2005-12-15
[QUOTE=ronmarley1]I see you've solved the problem.  However, you may want to try Firefox 1.5.  It smokes![/QUOTE]


Yeah, I read that many people found it really faster than the ubuntu's 1.0.7 package. But after some  rough benchmarks comparing WinXP's 1.5 against  Breezy's 1.07, both in my dual boot laptop, I don't notice any difference. 

Thus, as mine  newbie's TODO list  has many other unsolved items, for the time being I'll be stuck in 1.07, maybe until Dapper's official release.

---

