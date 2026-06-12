---
title: "Pidgin is freezing my computer"
date: 2009-03-17
forum: General Help
---

### Post by Hampster2 on 2009-03-17
Hello, I have Ubuntu 8.10 and when I load up Pidgen messanger it freezes my computer and the bottom and top toolbars disappear and there is all these images in the middle of the screen. It only happens when I load up that program. Do I have to fix up the video settings or what?

---

### Post by albandy on 2009-03-17
try deleting the .purple folder in your user folder and then configure the accounts again.

I'm using pidgin without problems.

---

### Post by Hampster2 on 2009-03-17
i cant find it.

---

### Post by albandy on 2009-03-17
well follow this steps, all your pidgin configuration will be deleted:

open a terminal (applications --> accesories --> terminal)
then type:
rm -rf .purple (this will erase your pidgin configuration, be carefull with this command, it could delete all your acount if you don't type it exactly)
then close the terminal
now open pidgin and will ask to configure you account

---

### Post by Hampster2 on 2009-03-17
Thanks all fixed.

---

