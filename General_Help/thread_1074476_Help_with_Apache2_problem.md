---
title: "Help with Apache2 problem"
date: 2009-02-19
forum: General Help
---

### Post by Greyfox67 on 2009-02-19
I don't see my post from yesterday so trying again:

I'm running Apache2 with PHP, MySQL.
I had downloaded an opensource program called Mindquarry for testing - suffice to say the test didn't go well.

Now my server is not finding my site with an error of "..not found on port 80."

My apache2.conf I finally commented out modules Included (mindquarry required Subversion and mod Perl)which got me past a DAVLock problem I was dealing with all morning. 

I have a ports.conf which includes ports 80 and 8080.
It seems server is not seeing my index.php

On a side note: I've tried editing my apache2.conf later and found I couldn't with everything under /etc owned by www-data. I've changing ownership by both and terminal and gui but keep receiving command "UID is 33 but should be 0 - not part of sudoers" - I am unable to change ownership at all and its frustrating me.

---

