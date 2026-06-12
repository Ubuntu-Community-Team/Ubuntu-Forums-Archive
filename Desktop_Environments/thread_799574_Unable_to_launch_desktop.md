---
title: "Unable to launch desktop"
date: 2008-05-19
forum: Desktop Environments
---

### Post by dESAI on 2008-05-19
Hi Good People :)

After about 10 unsuccessful attempts at installing Ubuntu 7.10, I finally succeeded last week. I was so happy as I'd almost given up after having so many problems, before, during and after installation. 

But this time it was a complete success! :)

Everything installed fine. I was able to install everything with no issues at all. Desktop effects, themes, window borders. The only thing I could not get working was the dual desktop display, but I was bouncing off the walls with happiness.

Yesterday I turned on the PC and instead of the login screen, I get a dos-style warning telling me something about the X Server (I don't have the PC here atm).

Now I think this is due to me installing the theme manager and new window borders.

I hope this can be repaired easily, if not then I'm sorry to say I'll have to give up on Ubuntu, for the near future anyway. I had so many problems with Ubuntu in the last 6 months, when I has 6.10 running on an old PC, it was great! I was so impressed I even persuaded my father to install it on his business computers.

I need to get this working so that I can provide him with support. Right now he has printer problems with PDF's, and I need to connect remotely, but I need a computer with Ubuntu working properly.

Sorry for the babble, I just want attention ;-)

Thanks in advance to everyone for your help.

---

### Post by didac on 2008-05-19
Sorry, we need more information. What does it exactly say?

You may try editing your configuration profile for X. Write in the prompt:

```
sudo nano /etc/X11/xorg.conf
```

In section "Device" comment all lines that begin with Option. Add a hash # at the beginning of each option line. Ditto for sections "Screen" and "Monitor"
Once your X starts again, uncomment one by one or use Preferences and Administration to set it to your liking.

Remember, from the command prompt you start X by typing

```
startx
```

If it comes to the worst, do

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure X.

If nothing works, post your xorg.conf here.

Don't give up. Linux is rewarding.

---

