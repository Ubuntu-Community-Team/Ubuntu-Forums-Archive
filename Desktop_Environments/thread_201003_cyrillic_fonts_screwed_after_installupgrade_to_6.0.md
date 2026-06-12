---
title: "cyrillic fonts screwed after install/upgrade to 6.06"
date: 2006-06-21
forum: Desktop Environments
---

### Post by teh on 2006-06-21
Hello, 

I have problems with cyrillic text on Ubuntu 6.06 LTS (the text looked fine with 5.10).
The problem concerns cyrillic text only. I'll just give you 2 links for your clarification ;-)

fine: [http://iseclab.net/fine.png](http://iseclab.net/fine.png)
not fine: [http://iseclab.net/notfine.png](http://iseclab.net/notfine.png)

"not fine" looked like "fine" with Ubuntu 5.10

Any comments/suggestions are appreciated ;-)

---

### Post by Alexander Nyakhaychyk on 2006-06-25
This problem [was discussed]("http://forum.ubuntu.ru/index.php?topic=2751.0") discussed on forum.ubuntu.ru.

Run "sudo dpkg-reconfigure fontconfig" enter your password and answer "Autohinter" on first question.

---

### Post by teh on 2006-06-25
That worked fine, thanks! ;-)

---

