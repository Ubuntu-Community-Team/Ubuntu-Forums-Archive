---
title: "Reconfigure up arrow key"
date: 2005-12-31
forum: Desktop Environments
---

### Post by digitaldeath on 2005-12-31
Hi all! New Kubuntu user here!
Kubuntu is great overall, however my up arrow key on my laptop is broken and using the console is often a pain when I want to browse through previously issued commands. Is there a way to configure this to my "page-up" key but only affect console/terminal input as I'd still like my page-up key to behave the way I expect it to in other applications?

Thanks in advance, and Happy New Year!

Digi.

---

### Post by PMO6022 on 2005-12-31
I don't have an answer for you but a quick google turned this up [http://www.delorie.com/gnu/docs/bash/bashref_92.html](http://www.delorie.com/gnu/docs/bash/bashref_92.html) It seems like it might have some info you need.

---

### Post by digitaldeath on 2006-01-14
Unfortunately this did not provide the required help. If anyone else has any suggestions, please post a reply.

Thanks,
Digital Death.

---

### Post by obibok on 2006-01-14
[QUOTE=digitaldeath]Hi all! New Kubuntu user here!
Kubuntu is great overall, however my up arrow key on my laptop is broken and using the console is often a pain when I want to browse through previously issued commands. Is there a way to configure this to my "page-up" key but only affect console/terminal input as I'd still like my page-up key to behave the way I expect it to in other applications?

Thanks in advance, and Happy New Year!

Digi.[/QUOTE]

You can play around with **/etc/inputrc** (or copy it to **~/.inputrc** for one user). Try uncommenting stuff or you may need to define your own.

What happens if you press *CTRL+V* followed immediately by *up-arrow*. Do you get any output (like ^[[A) or nothing?

---

### Post by digitaldeath on 2006-01-15
I'm not in front of my Linux box at the moment but I can tell you that the up arrow key doesn't do anything at all. It just simply doesn't work - it's not a Linux issue, it's a hardware issue as it's actually broken.

Regards,
Digital Death.

---

### Post by obibok on 2006-01-15
Too bad... but at least you know the source of the problem.

*solved*

---

