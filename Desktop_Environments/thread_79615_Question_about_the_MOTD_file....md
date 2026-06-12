---
title: "Question about the MOTD file..."
date: 2005-10-20
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-10-20
Not like it's a big deal, it just bugs the hell out of me.
Some program and/or script is adding "Linux cytrex 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux" to the top of my MOTD file.
Just a little thing that has been bothering me...any ideas of what may be doing this?

Hints/clues/howtos, all accepted. ;)

Regards,
Paul.

---

### Post by objorkum on 2005-10-20
Yes, it's /etc/init.d/bootmisc.sh

Check it out (it echoes uname -a into motd)

If you know how to use the "grep"-command, it's easy to find out such things.

Example, find all files in /etc that has "motd" in it:

sudo grep -R motd /etc/*

Voila, it finds bootmisc.sh

---

### Post by NewWithoutClue on 2005-10-20
Grep! Wonderful!

Thanks,
Paul.

---

