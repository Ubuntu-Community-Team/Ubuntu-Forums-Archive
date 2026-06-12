---
title: "I made a booboo"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by Jayfaas on 2008-01-13
I was messin around with the windows effects and I ended up setting the opacity to 0 and now when the windows pop up I can see the effect but no window.  How do I fix this?  Remember when ANY window comes up I cant see anything, just the opening and closing effect

---

### Post by Tenken on 2008-01-13
You could try switching to a CLI terminal with Ctrl+Alt+F1, then after logging in type

```
killall compiz
```

Which will stop compiz. Then hit Ctrl+Alt+F7 to return to your graphical terminal, if your window boarders don't appear when you open a program then open your terminal and type 

```
metacity &
```

That should get your windows back, and then maybe deleting your compiz configuration file before re-enabling compiz would do the trick.

---

### Post by Jayfaas on 2008-01-13
well thanks for the info but it didnt work.  I did killall compiz and it went to the next line
and I went back by ctrl+alt+f7 and tried to open it and it didnt work.  I dont remember if the opacity thing was in compiz though.  I went back to the ctrl+alt+f1 and typed metacity &, and it gave me the "Window manager error: unable to open X Display"

---

### Post by rune0077 on 2008-01-13
Holding down alt and scrolling the mousewheel up, will increase the opacity setting of the window your cursor is hovering over. So try guessing roughly where your window would be (actually you should be able to see it in the preview in the panel), then move the cursor there, hold down alt and scroll up with the mousewheel. Then fix things, since altering transparency this way will not be saved for next session.

---

### Post by Tenken on 2008-01-13
EDIT: Rune0077's solution is much easier.

---

### Post by Jayfaas on 2008-01-13
dude you are my savior.  THANK YOU.  I really didnt wanna have to reinstall

---

