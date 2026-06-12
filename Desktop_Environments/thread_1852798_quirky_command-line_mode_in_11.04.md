---
title: "quirky command-line mode in 11.04"
date: 2011-09-30
forum: Desktop Environments
---

### Post by Palartzski on 2011-09-30
i was successful in installing 11.04 on my home desktop. however, my monitor tends to be problematic and ive had to change the vertical and horizontal refresh rates before whenever ive installed different operating systems. therefore, i need to do the same thing with this installation of ubuntu. ive been following this tutorial:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

problem is, whenever i disable gdm (by running sudo /etc/init.d/gdm stop), i am taken to the text-only/command line mode. if i enter some sort of typical terminal command (ls, su, su <username>, etc.), i dont receive any response or output on my screen. all that happens is the cursor moves on to the next line. is there something i need to enable prior entering the command-line mode? there is not even a way for me to exit this screen and i always have to press ctrl-alt-del in order to restart my system. 

my overall goal is to be able to adjust my monitors vertical and horizontal refresh rates. however, in order to do so, i need to first be able to configure xorg because i currently do not have an xorg.conf file in my etc directory. from what ive researched to make these changes, i need to enter command-line mode regardless. any help would be greatly appreciated.

---

### Post by Toz on 2011-10-07
When at the login screen, press Ctrl+Alt+F1 to go to the first terminal. It will be a text screen and you should be able to login there. Are you able to enter the necessary commands here?

Also, can you still login to the graphical environment and get a viewable display? If so, you can open a terminal window and make the necessary changes. Logout for the changes to xorg.conf to take effect.

---

