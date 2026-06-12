---
title: "[SOLVED] GDM theme not installing"
date: 2007-08-20
forum: Desktop Environments
---

### Post by efriese on 2007-08-20
I've been playing with making a GDM theme. I think I've covered everything, but when I install it in the Login Window dialog it doesn't show up in the available themes. It doesn't give me an error message or any indication that the theme was not installed. When I try to install it again, it tells me that the theme is already installed. I've tried restarted gnome, but the theme does not show up.

I've attached the theme. Can anyone see why the theme is not showing up in the Login Window window? BTW, I'm using Feisty Fawn.

Thanks!

---

### Post by efriese on 2007-08-21
Any ideas?

---

### Post by efriese on 2007-08-21
If nobody knows why, can someone point me to another site where I can find out?

---

### Post by efriese on 2007-08-22
I found out why it wasn't working. The name of my xml file was not right. A tip for anyone who is having a problem installing a GDM theme, install gdmthemetester adn Xnest. gdmthemetester will actually give you an error to work with if something is not working with your theme. It also lets you see your theme without having to log out.

---

### Post by Kingstrum on 2007-08-24
While I am sorry no one was able to provide you with any help, I just wanted to say "thanks" as your post helped me solve the exact same issue. I finally got around to playing with a new install and setting up my own customized GDM theme. However, my experience was exactly the same: the theme selector let me load it (and it put everything in the right place, /usr/share/gdm/themes/), but it wasn't showing up as a selection option.

A little playing around with gdmthemetester and *poof* some of the stupid things I forgot to change in the XML & .desktop files were fixed and the theme was a-hoppin'!

Again, many thanks,
Kingstrum

---

