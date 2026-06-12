---
title: "Greeter screen / console lottery on lxde 16.04"
date: 2017-02-25
forum: Desktop Environments
---

### Post by shantiq on 2017-02-25
on a new computer Acer Aspire-XC-780 I installed 16.04 over Christmas and installed lxde as the Desktop Environment
and was greeted on start up with the lxde greeter screen with all the languages choices and DE choices
BUT THEN   after a few weeks it often on startup goes to the console asking for
Login:.....
Password:...
on the black console
I have no idea why that is; sometimes it goes to console and sometimes to lxde greeter screen; seems there is no rhyme nor reason for this
At first I was really put out as I had no idea what to do with console
Much fiddling/reading led me to work out I had to do this ...

```
sudo update-alternatives --config x-session-manager
```
pick lxde which is 4 and that saves it as default

Then everytime after [if it goes to console] 
Login:.....
Password:...
i need to enter:
startx


then it does open the way it did/and still does when the login screen/box appears

Question remains ...   why does it not always load the greeter screen/box but half the time only the console  ....puzzling

Any of you know the answer to this?


PS   this is what should come up each time and not the console
[[IMG]https://s7.postimg.org/8vgvbkz9z/IMG_1537.jpg[/IMG]]("https://postimg.org/image/8vgvbkz9z/")



THEANSWERIS:


when you are offered
Login:
Password:

[B]==============
=   ignore and do      =
=   CTRL+ALT+F7     =
==============

[/B]and the greeter screen will re-appear

---

