---
title: "titlebar disappears"
date: 2008-07-24
forum: Desktop Environments
---

### Post by gudgip on 2008-07-24
Hi,

I noticed that my titlebar was disappeared, so I go to ubuntuforum.org and search for a solution.
I found that this might work:
> metacity --replace
so I try it, and indeed it works, but every time I quit/start up my laptop, I've got thesame problem. If I enter metacity --replace again, it works again. 
Is there a solution to make it work always?

many thanks, gudgip

---

### Post by Potatoj316 on 2008-07-24
I think if you put those lines in your .bashrc it will execute that automatically, but that dosent really fix the problem, it just makes the symptoms go away

---

### Post by lordadi on 2008-07-24
Hi,

This is not really a solution but it should at least automate the "metacity --replace" part ;).

Create a launcher somewhere, right click on your desktop and then create a launcher. Put in metacity --replace as the command and name it something. After that, System > Preferences > Sessions and add your launcher to the list. After that, whenever you log in it will run the command! ;)

Cheers,

Lordadi

---

