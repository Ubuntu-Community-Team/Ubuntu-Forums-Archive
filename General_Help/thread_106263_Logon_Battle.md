---
title: "Logon Battle"
date: 2005-12-20
forum: General Help
---

### Post by scole on 2005-12-20
When i finally got the install program to run right it must have selected a different keyboard option. I had set it to American English for the layout but somehow it didnt stay there. all of my keys were off. For instance i would have to press g to get s. the problem is when i go to logon my settings are the awy they should be. So my username and password are both unattainable. I cant logon at all. Can i fix it or do i have to reinstall. If it helps i have winxp and puppy linux on my computer as well. maybe that can help. Is there any way for me to set up a new account from the logon screen????? HELP!!

---

### Post by localzuk on 2005-12-20
What type of keyboard is it you have, and what keyboard mapping are you using according to your /etc/X11/xorg.conf? It will be a line similar to 
```
    Option     "XkbModel"      "pc104"
```

---

### Post by scole on 2005-12-20
Well i didnt read the help file in UBUNTU. All i needed to do way boot up in recovery mode and # passwd scole to change it and all is well

---

