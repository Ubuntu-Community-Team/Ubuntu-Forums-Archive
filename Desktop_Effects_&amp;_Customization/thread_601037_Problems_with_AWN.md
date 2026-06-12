---
title: "Problems with AWN"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by aggierandy on 2007-11-02
Ok I installed awn using the HOWTO found here : 

[http://ubuntuforums.org/showthread.php?t=572019&highlight=install+awn](http://ubuntuforums.org/showthread.php?t=572019&highlight=install+awn)

It worked fine at first and I am not sure what happened but eventually it would not open from Applications-->Accessories-->Avant Window Navigator

So I followed the steps from the same HOWTO to uninstall, then I simply re-entered:

cd awn-curves
./autogen.sh && make
sudo make install

And I could run AWN again but now i cannot run AWN manager so I am stuck with the theme and icons before this whole debacle. How do I reinstall/fix AWN-manager

For reference I am using a Dell Inspiron 2200 with a fresh install of 7.10 

Here is what happens when I try to run awn-manager from the terminal

 randy@randy-laptop:~$ awn-manager
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 43, in <module>
    from awnTheme import AwnThemeManager
ImportError: No module named awnTheme

---

### Post by raul_ on 2007-11-02
You have to run avant-window-navigator

---

### Post by aggierandy on 2007-11-02
I have. It is running at the bottom right now. I simply cannot access the AWN-manager. I tried to run it through System-->Administration--> AWN manager, I have also tried right clicking and going to preferences as well as the terminal. No luck, Thanks for your quick response though

---

### Post by aggierandy on 2007-11-02
I solved it. For anyone that is having similar problems. Simply uninstall and run through all the install steps and it will work again. not really sure what happened but that fixed it. Thanks for help

---

### Post by boeing777 on 2007-11-02
i fixed it by reinstalling it too, it worked for a lot of problems.

---

