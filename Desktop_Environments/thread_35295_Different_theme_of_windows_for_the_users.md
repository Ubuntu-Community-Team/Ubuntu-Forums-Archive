---
title: "Different theme of windows for the users?"
date: 2005-05-18
forum: Desktop Environments
---

### Post by abmcr on 2005-05-18
[Here](http://abmcr.altervista.org/mostra.jpg) you see an image of the scite editor. When i launch it as root the look of the window is not the same of the user scite. How i do to change the root window appareance in the normal user theme? Thank you , ciao

---

### Post by lepetitalbert on 2005-05-18
Hello,

if you have a .scite file or folder in your home dir, copy it to /root.

Have a nice day.

---

### Post by Ptero-4 on 2005-05-18
[QUOTE=lepetitalbert]Hello,

if you have a .scite file or folder in your home dir, copy it to /root.

Have a nice day.[/QUOTE]
 Your problem is that the root user and your user account uses diferent window and application themes, to make them use the same themes you'll need to shut down X11 (from a terminal type sudo gdm stop , and enter your password when prompted) and then login as root (type exit and then in the commandline login box type root and the root password when asked) and then start X11 again (type startx). After doing this you'll be in gnome and you just need to install/apply the themes from the themes control panel as you did on your user account. after that logout (exit) from both X11 and the root account, login back (with your user account) and reopen X11 (sudo gdm start) relogin (in GDM) and you're done. Next time you open gnome apps as root they'll use your theme instead of the default one.

---

### Post by Stormy Eyes on 2005-05-18
[QUOTE=Ptero-4]Your problem is that the root user and your user account uses diferent window and application themes, to make them use the same themes you'll need to shut down X11 (from a terminal type sudo gdm stop , and enter your password when prompted) and then login as root (type exit and then in the commandline login box type root and the root password when asked) and then start X11 again (type startx). After doing this you'll be in gnome and you just need to install/apply the themes from the themes control panel as you did on your user account. after that logout (exit) from both X11 and the root account, login back (with your user account) and reopen X11 (sudo gdm start) relogin (in GDM) and you're done. Next time you open gnome apps as root they'll use your theme instead of the default one.[/QUOTE]

That solution is unnecessarily complicated. Instead, he should do the following:

[indent]1. Logout of X.
2. Hit CTRL+ALT+F1 to get to a terminal. Login.
3. **cd /usr/share/themes**
4. **sudo cp -R ~/.themes/* .**
5. **cd /usr/share/icons**
6. **sudo cp -R ~/.icons/* .**
7. **sudo /etc/init.d/gdm restart && exit**[/indent]

After that, themes for apps running as root should match the theme for apps you run as a user.

---

