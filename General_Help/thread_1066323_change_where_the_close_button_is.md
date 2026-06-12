---
title: "change where the close button is"
date: 2009-02-10
forum: General Help
---

### Post by kjhughes23 on 2009-02-10
yeah this sound stupid but I want to fix it
you know how in windows the min, max, and close buttons are on the right hand top corner, and in mac its the opposite.

Well, I installed a theme to look like mac and it put my buttons on the left and I switched the theme to human and it still is on the left, how can I fix this?

---

### Post by k3ttc4r on 2009-02-10
are you using emerald?

---

### Post by howefield on 2009-02-10
Open a terminal and type

```
gconf-editor
```

Navigate to apps > metacity > general and from the right hand window double click on "button layout" Change as required.

---

### Post by florinm on 2009-02-20
thanks Howefield. I had the same problem

---

