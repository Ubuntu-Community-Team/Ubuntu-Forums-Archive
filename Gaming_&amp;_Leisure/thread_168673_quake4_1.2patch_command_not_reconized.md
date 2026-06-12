---
title: "quake4 1.2patch command not reconized"
date: 2006-05-01
forum: Gaming &amp; Leisure
---

### Post by ndhskp on 2006-05-01
I just reinstalled Quake4 using the new 1.2 Linux patch.  It was installed to /home/username/.local/bin.  But typing "quake4 in the terminal says command not reconized.  I don't think that my /home/username/.local/bin is set up in the command path properly.  Can you help.

By the way the only bash file that I see is ".bash_history".

---

### Post by crane on 2006-05-01
[QUOTE=ndhskp]I just reinstalled Quake4 using the new 1.2 Linux patch.  It was installed to /home/username/.local/bin.  But typing "quake4 in the terminal says command not reconized.  I don't think that my /home/username/.local/bin is set up in the command path properly.  Can you help.

By the way the only bash file that I see is ".bash_history".[/QUOTE]
 Did you install as user or root?
When installed as root it will install a link to the quake4 script to /usr/local/bin. 
You could just copy it to there and it should work fine!

---

### Post by ndhskp on 2006-05-01
[quote=crane]Did you install as user or root?
When installed as root it will install a link to the quake4 script to /usr/local/bin. 
You could just copy it to there and it should work fine![/quote]Thank you very much for the advice, it worked perfectly.  I copied the symlinks that the game installs to /usr/local/bin.  This allowed me to leave the rest of the game on the much larger home partition.  And by the way I did install as user as I prefer my games to be running under user mode.

---

