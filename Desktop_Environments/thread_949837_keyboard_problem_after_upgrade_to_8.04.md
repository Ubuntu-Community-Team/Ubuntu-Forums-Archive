---
title: "keyboard problem after upgrade to 8.04"
date: 2008-10-16
forum: Desktop Environments
---

### Post by jukoz on 2008-10-16
Hey good people. Hey also to the not so good people. =)

I have a problem:
I upgraded my computer from xubuntu 6.06 to 8.04, using the upgrade tool. Apparently something is wrong with the new xorg, since my keyboard does not function properly:
In the login window, regardless if it is xdm or gdm, the keyboard does not function: the letter 'j' does not function, 'F1' acts as 'enter', 'ctrl', 'alt'... has no efect.
Most other keys work fine.

No, this is not a HW problem. The simptoms are the same with different keyboards, USB or PS/2.

Now, I have discovered, that this is the problem only in X, since if I boot in single user mode the keyboard works OK. Also, if I manage to make xorg.conf uncomprehensible for X, I get a nice working console. 

Also, if I manage to log in, I can change the keyboard layout with 'setxkbmap us' or 'setxkbmap si' form my native language keyboard.

If I change the keyboard layout in xorg.conf, there seems to be no change. So this must be something else.

Well, now comes the funny part: my username starts with the letter 'j'. That is why I cannot log in. If I use a different user, I can login and change the layout with setxkbmap and everything would be OK. But if I logout again, the layout will go back to the non functional.

Please help!!

Ajt!

---

