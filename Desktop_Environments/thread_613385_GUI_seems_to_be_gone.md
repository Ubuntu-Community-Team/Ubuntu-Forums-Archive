---
title: "GUI seems to be gone"
date: 2007-11-14
forum: Desktop Environments
---

### Post by rosspoko on 2007-11-14
I have an hp tx 1220 laptop and a 21" gateway 2275W monitor

I have just upgraded to ubuntu 7.10 today, and I was trying to get it to work with the larger monitor, which it never had in the past.  I found the screens toolin the Admin menu and set it to reflect my setup, though I had to choose 2200 or something as the model number of my monitor, because mine wasn't an option.  When I went to close the settings window, it told me that everyone had to log out for the settings to take effect, so I logged out.  Then it went to just a text based screen, like when its booting up or shutting down, and seemed to get stuck.  When I pressed keys, it would type what I pressed on the screen, but other than that it seemed to be frozen, so I turned the computer off and restarted.  Now, when I boot up, it goes normally until it gets to where the GUI should start and I enter my username and password.  Instead of doing that, it stays in the command line interface and asks me to sign in that way.  Even after I sign in, it stays in that mode.

---

### Post by taurus on 2007-11-14
Sounds like you need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
startx
```
What graphic card do you have in that laptop anyway?

---

### Post by rosspoko on 2007-11-14
My graphics card is an nVidia GeForce Go 6150.

That reconfiguration didn't work.  I didn't know the answers to some of the questions it asked.  After I typed startx it said Fatal Error: No screens found.  

Also, I have 2 ubuntu kernels to choose from in Grub.  One ends with 14 and the other ends with 16.  I've been using the 14 one because it is the first one on the list, which one is best to use?

---

### Post by rosspoko on 2007-11-14
nevermind, I restarted into ubuntu to see if I could have better luck with the config utility and it booted in low graphics mode.  From here I should be able to modify the settings correctly.  I'll post again if I still have problems.  Thanks for your help

---

