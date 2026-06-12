---
title: "Page Up/Down with mouse wheel"
date: 2008-10-19
forum: Desktop Environments
---

### Post by reglacken on 2008-10-19
Mouse wheel clicks move only a few lines. Grrrr.

Would rather each click move one page, but not obviously doable in preferences.

Doable ?

---

### Post by kerry_s on 2008-10-19
in firefox change:
mousewheel.withnokey.numlines :depends
mousewheel.withnokey.sysnumlines :false

the number depends on your screen size, i use 25 for mine.

---

### Post by zapp on 2008-10-19
Hi, 

you can try imwheel. I found it today and it works great. 

For example, if you want faster scrolling in firefox,
write this: 

```

"^Firefox"
None,Down,Down,10
None,Up,Up,10

```

or this

```

"^Firefox"
None,Down,Page_Down
None,Up,Page_Up

```

in your ~/.imwheelrc file. For evince write 

```

"^evince"
None,Down,Down,3 
None,Up,Up,3

```

Then start imwheel in the konsole. 

See this link for more information: 

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

(I only needed the imwheel parts)

---

