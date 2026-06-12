---
title: "How to set font settings as default?"
date: 2011-07-19
forum: Desktop Environments
---

### Post by a.toraby on 2011-07-19
Hi
I changed font settings in appearance utility today. But now desktop appearance and firefox fonts are too bad and I need to set it to default setting. How can I do that?
Thanks for any help.

---

### Post by jerrrys on 2011-07-20
can't you just change them back the same way?

---

### Post by a.toraby on 2011-07-20
> **jerrrys said:**
> can't you just change them back the same way?
I tried it. But in case of Firefox and nautilus when I change "application font size" neither Firefox and nautilus change anything.
By the way I tried Firefox options, Not only "appearance application" doesn't work well But also changing settings in Firefox options doesn't work any more :(
It is very discouraging that they don't include any "*default*" button in GUIs!!

---

### Post by jerrrys on 2011-07-20
have you by chance been playing with compiz?  if so open a terminal and enter

gconftool-2 --recursive-unset /apps/compiz

---

### Post by a.toraby on 2011-07-21
> **jerrrys said:**
> have you by chance been playing with compiz?  if so open a terminal and enter

gconftool-2 --recursive-unset /apps/compiz

Thank you jerrrys. I tried it, But nothing happened unfortunately!

---

