---
title: "Nameless windows appeared"
date: 2017-05-10
forum: Desktop Environments
---

### Post by asgard2 on 2017-05-10
Hi,

a so called nameless window (translated) appeared at my desktop.


How can there be such a window? 

Can I somehow identify the program?

Thanks

EDIT: sorry, I mistype the title, can it be changed?

---

### Post by vasa1 on 2017-05-10
Well, you're using a VM and so I'm not sure whether what I'm suggesting will work, but you can open a terminal and run *xprop*. Your cursor will change to "crosshairs" and you can then click on the nameless window. Output in the terminal may give you a hint.

---

### Post by asgard2 on 2017-05-10
Thanks for the hint, *xprop *is working.

But in the mean time, the window disappeared. I found an unfinished process pcmanfm and killed it, I guess that is the culprit. 

Maybe I can use *xprop *if this happens again.

---

