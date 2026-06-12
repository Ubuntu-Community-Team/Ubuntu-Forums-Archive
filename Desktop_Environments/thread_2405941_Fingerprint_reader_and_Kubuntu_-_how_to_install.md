---
title: "Fingerprint reader and Kubuntu - how to install?"
date: 2018-11-13
forum: Desktop Environments
---

### Post by anutosho on 2018-11-13
Hi folks,
I own a Thinkpad t420s and want to utilize the fingerprint reader. 
Before I had Mint installed, and after installing the fingerprint-tools I could use the fp reader for login after suspend, sudo at the console and so on.

Now I tried the same with Kubuntu 18.04 with partly success.
I can swipe my finger for sudo and for synaptic (the latter needs a following <Enter>, though)

BUT... When I try to login after suspend I have to enter my password AND after that I have to swype my finger, which is pretty secure, but it's definitely not what I was looking for. :???:

When I only enter my password or only swype my finger (after pressing <Enter>) I get the message "Aufheben der Sperre fehlgeschlagen" (Unlocking failed)
Only when I enter my password and press <Enter> the light at the fp reader goes on and I have to swype my finger to log in. Oddly enough I get the same error message, but then the desktop appears. 
The finger has to be recognized in spite of the error message. If I just swype SOME finger I cannot log in. When the lid of the notebook is closed (cause it's in the dock) I cannot log in at all.

I have no idea what I can do about it.

Installed packages are:
```
libpam-fprintd
fprint-demo
libfprint0
fprintd
```

I guess there is some config file to edit, but I have no clue which one.

---

