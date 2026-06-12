---
title: "Pidgin kernel panic!"
date: 2009-03-03
forum: General Help
---

### Post by wolterh on 2009-03-03
Though indirectly, pidgin causes my computer to completely freeze. This happens when I try to change my buddy display icon by clicking on the small icon to the lower right on the pidgin interface. The last things the pidgin debug said were:

```

(18:18:16) buddyicon: Converting buddy icon to png as /tmp/purpleEW59PU
(18:18:16) util: Writing file /home/wolter/.purple/icons/6e63936017015c4c18ae3127403679c5dc66f924.png
(18:18:16) buddyicon: Converting buddy icon to png as /tmp/purpleXH42PU
(18:18:16) util: Writing file /home/wolter/.purple/icons/ef6f0cf7209645660e6c60cb561890f1b7629d07.png

```

Now, that seems like a pretty harmless action, what pidgin is doing before my system crashes, but it is what triggers it. I suspect that the panic has very much to do with my wireless card, but I don't know how to extract more information from this error.

Thanks in advance!

---

### Post by ibuclaw on 2009-03-03
What messenger protocol are you using when you change your buddy icon?

Regards
Iain

---

### Post by wolterh on 2009-03-03
I am using bonjour, xmmp (gmail), and msn.

---

