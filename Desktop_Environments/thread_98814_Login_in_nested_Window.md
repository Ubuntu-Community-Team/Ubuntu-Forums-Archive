---
title: "Login in nested Window?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Sunnz on 2005-12-04
I have seen New Login in Nested Window in other distros, but not Ubuntu... does anyone know what I am talking about? I am wondering how could I get it.

My Ubuntu was installed using Hoary CD then upgraded to Breezy using apt.

---

### Post by endersshadow on 2005-12-04
```
sudo apt-get install xnest
killall gnome-panel
```

It'll be under Applications>System Tools>Login in a Nested Window

Hope this helps!

---

### Post by Sunnz on 2005-12-04
Thanks for the instant reply!

---

### Post by Sunnz on 2005-12-04
Now, is it possible to make it so root can log in under xnest?

---

### Post by endersshadow on 2005-12-04
Yes, it is possible.  Go to System>Administration>Login Screen Setup, click on the Security tab, and check the options "Allow root to login with GDM" and "Allow root to login remotely with GDM."

I would heavily advise against enabling this, though.  What are you trying to do that you can't do by using sudo or even su?

---

