---
title: "What do true and false do"
date: 2009-03-24
forum: General Help
---

### Post by camper365 on 2009-03-24
I was looking at the programs true and false, and I know that true does nothing, but does it successfully, and false does nothing and does it unsuccessfully, but what does it matter?
How do you find out if a program does anything successfully or not?
Is it in the system logs or something?

---

### Post by bodhi.zazen on 2009-03-24
true and false both do nothing and exit with a success and failure exit status respectively.

See info true and info false.

[http://tldp.org/LDP/abs/html/exit-status.html](http://tldp.org/LDP/abs/html/exit-status.html)

---

### Post by Bachstelze on 2009-03-24
They are mostly used in shell scripts, when you're syntactically required to put a command but don't want any actual action to be done, or as a placeholder for a not-yet-implemented function.

Also, you can define [font="monospace"]/bin/true[/font] or [font="monospace"]/bin/false[/font] as a user's default shell if you want to prevent that user from logging in on the system (since they're not actual shells and just do nothing, the user will be automatically sent back to the login prompt).

---

### Post by camper365 on 2009-03-25
thx

---

