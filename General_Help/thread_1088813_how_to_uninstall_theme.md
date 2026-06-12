---
title: "how to uninstall theme"
date: 2009-03-06
forum: General Help
---

### Post by suke231 on 2009-03-06
hi,everyone,i am an english learner,and I've been having ubuntu8.10 installed for about 4weeks,and as a newbie here i met much trouble about how to customize my pc.today i gave a theme named blue-joy a try,but when opening appearance there was always a hint below informing me "a gtk+ theme engine is required" which really annoyed me.after much effort i decided to uninstall the theme,but what is the best way of removing it.any help would be appreciated.:)

---

### Post by chriskin on 2009-03-06
isn't there a delete option at appearance?

edit :  or, of course, you can just install the gtk engine that is missing
since this looks like a downloaded theme, the author should be able to tell you which engine is missing

---

### Post by Therion on 2009-03-06
> **suke231 said:**
> ... but what is the best way of removing it.
Right-click on the theme in the Appearance Manager and then click on "Delete".

---

### Post by suke231 on 2009-03-06
yeah,i found the icon "delete"
indeed it is a downloaded theme,but the installation instruction of the theme didn't show me which specific theme engine would be needed.so how can i make it happen.

---

### Post by chriskin on 2009-03-06
> **suke231 said:**
> yeah,i found the icon "delete"
indeed it is a downloaded theme,but the installation instruction of the theme didn't show me which specific theme engine would be needed.so how can i make it happen.

if you mean about the delete, just click it

if it is about the engine, show me where you downloaded it from and let me some seconds to search around

---

### Post by suke231 on 2009-03-06
[http://gnome-look.org/content/show.php/Blue-Joy?content=73387](http://gnome-look.org/content/show.php/Blue-Joy?content=73387)
i mean make the theme engine installed completely.
many thanks for your kindness.

---

### Post by chriskin on 2009-03-06
it is the gtk2-engines-pixbuf package that you might be missing

try finding it in synaptic or try the command sudo apt-get install gtk2-engines-pixbuf

---

### Post by suke231 on 2009-03-06
as you said i got that theme engine,but after that nothing happened,should i need to try a logout?

---

### Post by suke231 on 2009-03-06
thank you for your answer.

---

### Post by chriskin on 2009-03-06
a restart is probably needed, but i have never done it before, so i do not know

restart the computer to be sure, though :)

---

### Post by suke231 on 2009-03-06
well,whatever happened after a restart thank you all the same.now i have to go to bed,and probably i can see if it works out this problem with your method.whenever i got the solution i will share with you.many thanks for your time.:P

---

