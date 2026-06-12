---
title: "Can't edit my desktop"
date: 2006-07-06
forum: Desktop Environments
---

### Post by polloz on 2006-07-06
hello,

i have the following problem. i did a clean isntall of dapper in my laptop. it all went smoothly. then i wanted to add the "system, home, trash" icons on my desktop, so i sudo gconfig to turn this options on. the thing is that once they are turned on, still anything happens on my desktop. also, when i try to edit my menus with alacarte,  for example renaming an application or removing it, it allows me to do so but when I click close my changes do not take place. when i open alacarte again, it is as if i've never done any changes.
are this problems related? what do i need to do to fix this? help please.

thanks.

---

### Post by aysiu on 2006-07-06
Have you tried this? ```
sudo chown -R polloz:polloz /home/polloz
``` This assumes, of course, that your username is *polloz*.

---

### Post by polloz on 2006-07-06
thanks, it did work!!! now i can edit my menus as i wish. the desktop icons problem is still there i guess.

thanks a lot!

---

### Post by aysiu on 2006-07-06
Try Alt-F2 ```
gconf-editor
``` and going to Apps > Nautilus > Desktop and unchecking the Volume Visible option.

---

### Post by polloz on 2006-07-06
it worked. now i see mi desktop icons. you are the men! thanks a lot, little things like this are what make people happy. thanks men.

---

