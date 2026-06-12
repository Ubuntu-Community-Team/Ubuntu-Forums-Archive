---
title: "[SOLVED] Conky not reporting linkstatus"
date: 2007-10-27
forum: Desktop Environments
---

### Post by lsutiger on 2007-10-27
I just installed Gutsy and when I run conky, the linkstatus is not reporting. It has "{linkstatus...}" on the screen. I will attach a screenshot to see it and it also has the conkyrc file open to the area in question.
This was working fine in Feisty.
Any ideas?
Thanx in advance!

---

### Post by lsutiger on 2007-10-28
Bump!

---

### Post by scorbz on 2007-11-03
Bonjour,

La variable linkstatus n'éxiste plus pour Conky 1.4.8
Essai plutôt "*wireless_link_qual*" ou "*wireless_link_qual_perc*" (en pourcent).

Les variables disponibles sont [[COLOR="Blue"]là[/COLOR]]("http://conky.sourceforge.net/docs.html").

Cordialement

---

### Post by lsutiger on 2007-11-03
Merci...parlez englais?

Thank you I got it!

---

### Post by holodad on 2007-11-25
Hi

If you have the linkstatus problem on Gutsy with conky, it's quit normal. If you see the word linkstatus instead of the value of reception, you have to replace linkstatus by wireless_link_qual_perc in your .conkyrc file
The variable linkstatus doesn't exist anymore on Gutsy. It's as been replaced by ${wireless_link_qual_perc eth1}
So edit you conkyrc file and change ${linkstatus ethX} % by ${wireless_link_qual_perc ethX}

Cheers

---

