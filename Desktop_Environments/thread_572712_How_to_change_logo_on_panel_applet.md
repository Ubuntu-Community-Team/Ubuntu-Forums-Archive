---
title: "How to change logo on panel applet"
date: 2007-10-10
forum: Desktop Environments
---

### Post by GoranI on 2007-10-10
I`m using Ubuntu 7.04.  I want to change ubuntu logo for example star, and I don`t want to do this with theme changing. What I have to edit to do this ?

---

### Post by ryanVickers on 2007-10-10
I know - wait a second... ;)

Ok, got it!:

> 
 how to install
System tools->configuration editor->Apps->Panel->Objects
Find the object where 'object-type' is equal to 'menu-object'
check 'use_custom_icon'
set the value of 'custom_icon' to the path of the button.


---

