---
title: "Can't change greeting on login screen"
date: 2007-10-30
forum: Desktop Environments
---

### Post by gluonman on 2007-10-30
Aloha!
   I am a gutsy user and I am having a small problem with my login screen options. Everything is working fine, except that every time I try to change the default greeting, "Welcome," to something of my choice, it automatically switches back to the default behind my back regardless of the login theme. Why does this happen? And what does it mean that underneath the bar where you enter your custom greeting it says, "%n will be replaced by hostname"?
   Mahalo.

---

### Post by Prince_Rainbow on 2007-10-30
I have the same problem: not only will the greeting go back to "Welcome" after a reboot (although the option "Custom" is still set, only the text has been reverted to your standard 'Welcome'), but I can not even disable the sound played when I log in (right now the box for 'Login successful' is unticked and the sound in the disabled box is set to none, but if I enable that box I get the login sound twice), and the background colour visible upon loging in is still orange although I set it to black... in other words, I can not change the default settings.
I can, however, change the theme of the login manager.

And to reply to gluonman: the "%n will be replaced by hostname" means that if your machine is called Laptop or Ubuntu-box for instance and you write a welcome message like "Welcome to %n", a user wanting to log in would see "Welcome to Laptop" or "Welcome to Ubuntu-box" at the login screen.

I am running Ubuntu 7.10 on an AMD64, clean install.

Thanks a lot
PR.

---

### Post by gluonman on 2007-10-31
Looks like I'm not the only one. I still haven't figured it out. Let me know if you come up with something.
Thank you.

---

### Post by gluonman on 2007-11-09
I just discovered that you can manually change your custom greeting by going into terminal, typing gksudo gedit /etc/gdm/gdm.conf-custom. It will open up the text page where the information is located. You will see:

[greeter]

BackgroundType=1

DefaultWelcome=false

You just need to add a line that says:

Welcome=[whatever you want].

Then the next time you reboot your computer, your desired welcome should show.

---

