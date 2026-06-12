---
title: "[SOLVED] 'Show Hidden Files' option gone in Nautilus"
date: 2005-07-08
forum: Desktop Environments
---

### Post by manicka on 2005-07-08
I was recently playing with starting multiple sessions and had a system freeze.

Now in Nautilus I no longer have the option to choose 'Show Hidden Files' when I right click in a directory in Nautilus. It's just disappeared from the menu.

Has anyone experienced this before? how can I get this option back?

P.S. I still have this option from the view menu and control -h, but I really want it back in the context menu.

---

### Post by mtron on 2005-07-08
I can only offer a partial solution:

open the gconf editor (Apps - System Tools) and navigate to 
desktop - gnome - file_views and check "show hidden files" 

But i think this key always displays the hidden files... At least worth a try.

---

### Post by manicka on 2005-07-08
So I created and logged in as a new user and it is missing from that users context menu as well, which indicates a system wide setting problem.

Any ideas?

---

### Post by manicka on 2005-07-08
Was I actually able to do this before or am I going nuts?

---

### Post by manicka on 2005-07-09
Okay, so I was going mad and the option was never there to begin with.  8-[ 

Does anybody know a good nautilus script for the job of showing hidden files?

---

