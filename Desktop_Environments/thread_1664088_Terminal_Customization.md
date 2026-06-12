---
title: "Terminal Customization"
date: 2011-01-10
forum: Desktop Environments
---

### Post by dodo3773 on 2011-01-10
I recently made some tweaks to my terminal by adding this to my .bashrc

```
PS1="\u\[\033[m\] \w\[\033[m\]\$ "
```It shortened things up a bit which is nice. The problem I have is that when I sudo -s etc.. The "$" does not switch to "#" is there any way to still get a "#" with these types of customizations? What am I missing?

---

