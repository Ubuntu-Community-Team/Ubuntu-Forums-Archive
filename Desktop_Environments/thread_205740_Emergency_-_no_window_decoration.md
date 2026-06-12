---
title: "Emergency - no window decoration"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Dubbayoo on 2006-06-28
I just processed some pkg upgrades that came out today for Dapper - libgtk, etc - now I have no window decoration at all. The app windows have no borders. How do I fix this? 

Desperate

---

### Post by dmizer on 2006-06-28
not sure how window decoration is an emergency.  you can still use your system, and your data isn't in jeapordy.

have you tried working with your theme settings?  it could be that your gtk theme isn't compatable with the new version installed.  try selecting a different border for your theme, or selecting a completely different theme.

---

### Post by Dubbayoo on 2006-06-28
You may not consider it an emergency however I am free to to decide otherwise. Your suggestion did not make any difference, but thanks anyway.

---

### Post by aysiu on 2006-06-28
Try just resetting your themes completely: ```
mv ~/.themes ~/.themes.old
``` Then Control-Alt-Backspace to reset the X server (warning: this will log you out and close all your applications).

---

### Post by Dubbayoo on 2006-06-28
[QUOTE=aysiu]Try just resetting your themes completely: ```
mv ~/.themes ~/.themes.old
``` Then Control-Alt-Backspace to reset the X server (warning: this will log you out and close all your applications).[/QUOTE]

no such luck there either. :(

---

