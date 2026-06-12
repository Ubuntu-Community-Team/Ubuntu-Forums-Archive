---
title: "Quake 4"
date: 2008-05-04
forum: Gaming &amp; Leisure
---

### Post by psychofish25 on 2008-05-04
I am running Quake 4 on Ubuntu through the linux runtime and I have come across a strange problem. Whenever I click multiplayer and create a server, it comes out of full screen and into windowed mode, and refuses to accept mouse events. It is impossible to play multiplayer like this and the only way to exit is alt-f4. Can someone please help me?

---

### Post by Perfect Storm on 2008-05-04
Something to try/do;

1) Disable Compiz
2) Run quake4 via terminal and check its output.

---

### Post by psychofish25 on 2008-05-04
well i found disabling "compiz.real" does the trick, but when I kill it, my window tops go away, which I need. Otherwise I need to log out and return everytime i play quake4 online. Is there a way around this?

---

### Post by Perfect Storm on 2008-05-04
<alt>+<F2>
```
metacity --replace
```

*launch Quake4 happily*

when done.

<alt>+<F2>
```
compiz --replace
```

---

### Post by psychofish25 on 2008-05-04
Oh wow thanks

---

