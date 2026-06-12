---
title: "Xgl/Compiz hibernating issue"
date: 2006-08-16
forum: Desktop Environments
---

### Post by RoyCowboy on 2006-08-16
I'm having some problems with Xgl/Compiz after hibernating. Look at the shadows on the menus in this picture [Screenshot.png]("http://per-henrik.no/Screenshot.png")

What could cause theese "missing" shadows?

---

### Post by art on 2006-08-16
That should be easy to fix, 
```
killall cgwd
cgwd&
```
but is that the only issue you have? In my case atfer hibernation the switcher and scale were flickering. Do you have that?

---

