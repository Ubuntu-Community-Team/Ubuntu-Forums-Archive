---
title: "Some Gnome apps have broken icons"
date: 2009-02-18
forum: Desktop Environments
---

### Post by josepcoves on 2009-02-18
Hi,

I have Ubuntu 8.04 LTS installed on my Laptop. A couple of weeks ago some Gnome apps got broken icons. For instance, "file archiver", "Documents viewer" or "Compiz desktop effects advanced tool" have some of their icons broken. I send an attached image to show my problem.

I've tryed to create a new user and this user has no broken items in any application, so I suspect the problem should be some of my SO user configurations files. 

Any ideas of what I could check?

Many thanks

Josep

---

### Post by Fzang on 2009-02-18
I've had same problem and haven't found a cure so far. I think it happened when I installed some theme engines

Bump for this post, I'd like to know how to fix this as well

Off topic: do you mind telling me what fonts and configuration you use? They look amazingly smooth :)

---

### Post by josepcoves on 2009-02-18
Hi Fzang,

I use clearlooks for controls and Milk2.0 for window borders. My font type is Sans 8. ;)

The only workaround I found to fix the problem is creating a new SO user...

Hope somebody helps us!

---

### Post by josepcoves on 2009-02-26
Hi I found the solution of the problem:

In your local folder (/home/user/), rename the .local/share/icons/hicolor folder to disable it:

$ rm .local/share/icons/hicolor .local/share/icons/hicolor_old

Hope it helps someone!

---

