---
title: "Remapping Backspace in Konsole"
date: 2008-05-05
forum: Desktop Environments
---

### Post by cmnorton on 2008-05-05
I've looked at the Konsole configuration settings. I would like to be able to have a backspace delete, rather than its default setting. These settings occur with the Gnome terminal. How do I configure in Konsole?

---

### Post by Xiong Chiamiov on 2008-05-05
Ok, according the the xmodmap man page, it looks like you need to run
```

xmodmap -e "keysym BackSpace = Delete"
echo "XTerm*ttyModes:  erase ^?" | xrdb -merge

```

I'm not sure if that's all you have to do or not, so tell me how it goes.

---

### Post by cmnorton on 2008-05-06
I am going to keep this, but I reset in Konsole by making the term type a vt100. When I get a chance, I'll put it back to a linux term and try this command.

Many thanks.

---

