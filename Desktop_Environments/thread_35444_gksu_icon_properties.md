---
title: "gksu icon properties"
date: 2005-05-18
forum: Desktop Environments
---

### Post by vanaedium on 2005-05-18
Hi
I need an icon on desktop which launch nautilus in browser mode:
On shell you'll see

sudo nautilus --browser

but on the icon properties if I set 

gksu nautilus --browser

nothing happens because the option --browser is refer to gksu and not to nautilus as I would

Ideas?
Thanx

---

### Post by codejunkie on 2005-05-19
if your wanting to run nautilus as root in browser mode just add a launcher to the desktop with the command: gksudo nautilus then in nautilus click edit preferences under the Behavior tab check Always open in browser windows restart nautilus then it will always open in browser mode hope this helps.

---

### Post by vanaedium on 2005-05-19
thanx works!!!!!!!
 :)

---

