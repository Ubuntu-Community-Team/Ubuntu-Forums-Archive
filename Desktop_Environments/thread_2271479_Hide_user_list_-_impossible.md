---
title: "Hide user list - impossible?"
date: 2015-03-30
forum: Desktop Environments
---

### Post by Jaxilian on 2015-03-30
Hi
Does anyone know why it's impossible to change so the user list isn't visible? This setting is a great security improvement if it works.

I have tried creating the file 01-mysettings under /etc/dconf/db/gdm.d/ with the disable-user-list=true - **which fails**
I have tried the override setting under /usr/share/glib-2.0/schemas/20_ubuntu-gnome-default-settings.gschema.override with same disable-user-list=true - **which also fails**
I have tried the dconf tool and set it there - **but fails too**
I have tried directly set it with sudo gsettings set org.gnome.login-screen disable-user-list true -** that fails too**

What am I doing wrong? 
I am using Ubuntu Gnome 15.04

---

### Post by Jaxilian on 2015-03-30
I found the answer myself

link: [https://ask.fedoraproject.org/en/question/9875/how-do-i-disable-user-list-in-gdm/](https://ask.fedoraproject.org/en/question/9875/how-do-i-disable-user-list-in-gdm/)

I missed adding the below ones into  /etc/dconf/profile/gdm

user-db:user
system-db:gdm

After that it worked.

---

