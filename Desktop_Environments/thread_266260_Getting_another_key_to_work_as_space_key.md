---
title: "Getting another key to work as space key"
date: 2006-09-27
forum: Desktop Environments
---

### Post by ulriks on 2006-09-27
Hi All,

I have an older laptop where the space key is not working. Does anyone know how I can set up (k)ubuntu or change the keyboard layout, so Ctrl-Backspace (for instance) works as the space key?

I have previously just pasted the space, but that really sux when one copy-paste other things.

Thanks

---

### Post by Jussi Kukkonen on 2006-09-27
take a look at xmodmap and xkeycaps -- they should help.

---

### Post by ulriks on 2006-10-04
Thanks! xkeycaps works great!

However, the changes made are not saved when I logout, so I have to   run xkeycaps every time I start a new session.

Any idea why this is, and more to the point, how I can avoid it?

---

### Post by nikhilk on 2006-10-04
Under the section "Write Output" at [http://www.jwz.org/xkeycaps/man.html](http://www.jwz.org/xkeycaps/man.html) you will find what you want.

---

