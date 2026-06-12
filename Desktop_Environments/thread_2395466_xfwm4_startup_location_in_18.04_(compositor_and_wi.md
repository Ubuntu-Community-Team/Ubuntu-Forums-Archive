---
title: "xfwm4 startup location in 18.04 (compositor and window manager)"
date: 2018-07-02
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2018-07-02
[SIZE=3][FONT=arial]**Question: Where is the startup compositor and window manager specified in the system files of Xubuntu 18.04?**

I have been using xfce with compiz for many years, since it really  increases my productivity. (Please don't tell me this is nonsense - I  love xfce and have a very powerful machine!)

**Edit:** Copy /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml to ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml as suggested [here]("http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html"), and replace[SIZE=3][FONT=arial] "xfwm4" with "compiz". RESTART your system after that, do not simply log out! [/FONT][/SIZE] [/FONT][/SIZE]

---

