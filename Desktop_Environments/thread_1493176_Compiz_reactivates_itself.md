---
title: "Compiz reactivates itself"
date: 2010-05-25
forum: Desktop Environments
---

### Post by mpw on 2010-05-25
Hello,

as my laptop is getting older and slower, I deactivated the nice window effects. System -> propieries -> appereance -> no effects

But Ubuntu reactives them after the next reboot!

Is there any configuration file or do I have to uninstall compiz-core complety?

Thanks for help.

Bye
MPW

---

### Post by F1R3H4CK3R on 2010-05-25
Try this in terminal:
> $ sudo apt-get remove compiz-core
> $ sudo apt-get remove compiz-config
> $ sudo apt-get remove compiz-config-settings

---

### Post by mpw on 2010-05-25
Thanks.

This was the hart way, but it worked:-)

I think it was the compiz-config-settings which overrode the general settings to not use compiz.

However

Solved and closed

---

### Post by mpw on 2010-05-26
Okay, this was just a big fail.

After rebooting my laptop, I just had NO window manager.

The windows where all undecorated and I had to start metacity manually.

In System -> Utilities -> Appereance -> Effects none of the three points where checked.

How can Ubuntu be that stupid?

I tried that way: [http://wiki.ubuntuusers.de/compiz](http://wiki.ubuntuusers.de/compiz) (german, but the orders are the same of course).

I had to reinstall compiz now, because the system was unusable.

How can I set the standard window manager? I want metacity! Which works great, if activated manually. 

Thanks for advice.

Bye
MPW

---

### Post by F1R3H4CK3R on 2010-05-27
Your welcome, always helping with waht I know. :)

---

### Post by Timmer1240 on 2010-05-27
You need this [http://allmyapps.com/app/ubuntu-9.10/fusion-icon-compiz-fusion-icon](http://allmyapps.com/app/ubuntu-9.10/fusion-icon-compiz-fusion-icon)       then after its installed go to applications system tools leftclick add to panel then when its in the panel left click it and you can switch to metacity window manager hope this helps!

---

### Post by mpw on 2010-05-29
Timmer1240,

thanks for the idea. But that Icon is for compiz - I want metacity :-)

Bye

---

### Post by Bobhuber on 2010-05-29
> **mpw said:**
> Timmer1240,

thanks for the idea. But that Icon is for compiz - I want metacity :-)

Bye
You didn't read the previous post.The Compiz icon allows you to switch between Metacity or Compiz.

---

### Post by Timmer1240 on 2010-05-29
The compiz fusion Icon allows you to switch to the metacity window manager!Just install it it does work for what you want to acomplish I have it I can switch from compiz to metacity at will with the Icon!

---

