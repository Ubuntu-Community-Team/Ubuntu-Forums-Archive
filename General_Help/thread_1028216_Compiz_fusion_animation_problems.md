---
title: "Compiz fusion animation problems"
date: 2009-01-02
forum: General Help
---

### Post by Jameshardy88 on 2009-01-02
Recently all of my animations that i have set up disappeared and now any attempt i make to create new ones do not work. i do not not what caused them to vanish however i may have installed a compiz theme i dont know if that makes a differences. I was wondering if their was a way to reset compiz to its default values or anything as im am by no means a wiz on creating the animations (i just changed the animation types on the existing ones)

any help would be appreciated, thanks,

James

---

### Post by Forlong on 2009-01-02
In case you're on GNOME, you can reset your Compiz settings like this:

```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

