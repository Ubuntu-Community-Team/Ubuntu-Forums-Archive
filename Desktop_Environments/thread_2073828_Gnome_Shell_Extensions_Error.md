---
title: "Gnome Shell Extensions Error"
date: 2012-10-20
forum: Desktop Environments
---

### Post by faustus34 on 2012-10-20
I recently upgraded 4 machines to Ubuntu 12.10. 1 machine is 32 bit, the 3 others are 64 bit. On two of the 64 bit machines I am getting this error when visiting the Gnome Extensions.org website which worked fine before the upgrade:

"You do not appear to have an up to date version of GNOME 3. You won't be able to install extensions from here. See the about page for more information."

I am using Firefox on all machines. I have deleted all extensions from both .local/share/gnome-shell/extensions and /usr/local/gnome-shell/extensions and this did not fix the issue. 

Does anyone know of a fix for this? I've read about resetting all of my gnome settings but I'd rather not do that as it is a bit drastic and some people have confirmed that it didn't work anyway. 

Thanks

EDIT - I got my extensions working by using an alternate profile in firefox: 

open a terminal and type: firefox -P and then create an alternate profile and use that to install the extensions. 

It's odd that my default profile is causing that issue on two machines. If anyone has a more specific answer, please let me know. I will continue to look into it.

---

### Post by pedro.nariyoshi on 2012-10-23
I'm having the same problem. Did you file a bug report?

---

