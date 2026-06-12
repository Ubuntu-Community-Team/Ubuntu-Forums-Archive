---
title: "Logoff Command"
date: 2008-05-21
forum: Desktop Environments
---

### Post by dummyapple on 2008-05-21
I was in my desktop environment and accidentally exited fluxbox. now I cannot open windows etc

So I need to logout via command line. How can I logout? I don't want to reboot or shutdown (it's a server)

---

### Post by VMC on 2008-05-21
> **dummyapple said:**
> I was in my desktop environment and accidentally exited fluxbox. now I cannot open windows etc

So I need to logout via command line. How can I logout? I don't want to reboot or shutdown (it's a server)
Type logout or Ctrl+d

---

### Post by kerry_s on 2008-05-21
> **dummyapple said:**
> I was in my desktop environment and accidentally exited fluxbox. now I cannot open windows etc

So I need to logout via command line. How can I logout? I don't want to reboot or shutdown (it's a server)

just type> **exit**
but, if you want to get back in just type> **startx**

---

### Post by pewpewaliens on 2010-03-05
> **kerry_s said:**
> just type> **exit**
but, if you want to get back in just type> **startx**

Thanks alot! I was stuck in and xterm-only login

---

### Post by aeon.flux on 2010-04-28
what command sould i type into applet, if i want it to do the same as Ctrl+Alt+Delete? (menu where i can choose from shut down, suspend, hybernate etc)

---

### Post by kerry_s on 2010-04-28
> **aeon.flux said:**
> what command sould i type into applet, if i want it to do the same as Ctrl+Alt+Delete? (menu where i can choose from shut down, suspend, hybernate etc)

for what desktop/window manager?

in gnome i think it's "gnome-session-save --logout", check the man page.

---

### Post by aeon.flux on 2010-05-01
no, i wanted it for avant windows navigator, because it supports only log out windows, then u can only log out, or switch user. i;ve installed lucid lynx yesterday and the applet know some more commands by default, so i dont need this anymore

---

### Post by elvis-nguyen on 2010-11-24
> **kerry_s said:**
> for what desktop/window manager?

in gnome i think it's "gnome-session-save --logout", check the man page.

This is exact what i am looking for. Thanks!

---

### Post by rajun198 on 2012-03-30
To logout from command line in ubuntu 11.10 its *"gnome-session-quit* "

---

### Post by RCress on 2012-06-13
> **rajun198 said:**
> To logout from command line in ubuntu 11.10 its *"gnome-session-quit* "

Thank you so much! I tried the Gnome/Openbox setting when I logged in to 12.04. It only showed me the desktop. I was able to bring up the terminal and Firefox to view your post. I'm set to log in automatically, so even restarting my computer would not have taken me to a working desktop. Thanks for saving me from having to reinstall!

Why does Ubuntu include the Gnome/Openbox as a log-in option when it doesn't work? Doesn't seem very newbie friendly.

---

