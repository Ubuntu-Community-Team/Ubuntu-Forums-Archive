---
title: "how do i disable movment of gnome panels for my mom?"
date: 2008-01-06
forum: Desktop Environments
---

### Post by yigal100 on 2008-01-06
hello all,

I've installed Ubuntu for my mom and she always manages to move the gnome panels to the side and  than she asks me to fix that.
I've tried to use gconf-editor to make the location of panels fixed however it gives me an error.
(her user isn't an admin one,  mine is. maybe that's related).
I've also managed to make the appropriate keys to be mandatory when running gconf-editor with sudo, however it _doesn't_ affect my mom's account... 

what else can i do?

 [btw, I HATE that gconf utility. what a stupid idea! the last thing Linux needs is a MS style registry....... it should be abolished!]

thanks,
Yigal

---

### Post by roaldz on 2008-01-06
> **yigal100 said:**
> hello all,

I've installed Ubuntu for my mom and she always manages to move the gnome panels to the side and  than she asks me to fix that.
I've tried to use gconf-editor to make the location of panels fixed however it gives me an error.
(her user isn't an admin one,  mine is. maybe that's related).
I've also managed to make the appropriate keys to be mandatory when running gconf-editor with sudo, however it _doesn't_ affect my mom's account... 

what else can i do?

 [btw, I HATE that gconf utility. what a stupid idea! the last thing Linux needs is a MS style registry....... it should be abolished!]

thanks,
Yigal

Don´t know about the panels and the gconf, but I know that you can´t have an ¨admin¨ account, unless you´re logging in everywhere as the ¨root¨ user. Doing that is a very, I repeat, VERY bad idea. Just stick with a normal user account, and use sudo and gksu. For your mom to be able to use sudo, you should add her user to the ¨sudoers¨ group if I´m not mistaking.

Good luck,

Roald

---

### Post by yigal100 on 2008-01-08
thanks for the advise, although I don't agree with it fully.
I came to Ubuntu from Debian and the lack of a root user is sometimes very annoying for me. I agree that for regular users it probably shouldn't be available, but for someone that knows what he's doing, the constant typing of "sudo" can grow tiresome very quickly.

what I meant in my original post is that my mom's user can't use sudo because it's not in the admins group.
I don't intend to add her user to the admins group anyway, as I prefer her profile to be with as little permissions as possible.

---

