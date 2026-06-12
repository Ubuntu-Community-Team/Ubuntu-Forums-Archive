---
title: "midnight commander color scheme modification"
date: 2009-01-30
forum: General Help
---

### Post by maclenin on 2009-01-30
I would like to modify the color scheme of midnight commander ("mc") - which I run via the terminal (xterm) in Intrepid.

I have already tried changing the color scheme, by:

1. appending the following...

```
[Colors]
base_color=gray,black
normal=yellow,black
menu=yellow,gray
viewunderline=black,green
editnormal=white,black
editmarked=black,white
menuhot=red,gray
directory=brightred,gray
...
```

...to ~/.mc/ini (mc configuration file) - to no avail.

2. taking a peek at other suggestions, namely...

```
sudo nano /etc/X11/app-defaults/XTerm-color
```

...to modify the VT100 color settings - which I don't feel knowledgeable enough to toy with.

I continue searching...thanks for any suggestions.

---

### Post by kerry_s on 2009-01-30
that don't look right, it's suppose to be 1 line, example:

```
base_color=normal=,default:selected=,:marked=,default:markselect=,:menu=,:menuhot=,:menusel=,:menuhotsel=,:dnormal=,:dfocus=,:dhotnormal=,:dhotfocus=,:input=,:reverse=,:executable=,default:directory=,default:link=,default:device=,default:special=,:core=,:helpnormal=,:helplink=,:helpslink=,:
```

thats the line for transparent.

---

### Post by maclenin on 2009-01-30
**kerry_s:**

Thanks!

Essentially, the color scheme components need to occupy a single line in the ini file and be separated by "**:**".

For (additional) example:

```
[Colors]
base_color=gray,black:normal=yellow,black:menu=yellow,gray:viewunderline=black,green:(and so on)
```

**[SOLVED]**

---

