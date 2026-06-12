---
title: "KDE GUI doesn't load on boot"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by danpaquin on 2008-02-22
Hi there guys - having a little trouble with my first install of linux (KUbuntu 7.10).

Well, the installation went very smoothly, and the OS loaded without a hitch until I tried to to install compiz-fusion.  Now, when I boot to KUbuntu I get errors such as: usplash: init 1024x768 failed, and then it goes through a few other resolutions and they all fail, and it returns me to the command prompt without ever loading the GUI. 

When I tried to install compiz fusion I used the following code from the ubuntu website and I input it into the "Run Command..." prompt from the "start" menu. (Was that the wrong place to enter this code?  Did I miss a "-" or a "_" or something and that's what nuked it?)

```
sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra 
compizconfig-settings-manager emerald librsvg2-common
```

Oh - and the *very* last thing I did before I reboot and got this error was to enter the terminal by using the <ctrl>+<alt>+Fn to enter the terminal - and I couldn't figure out how to exit out of it to the desktop again so I reboot from there - did that perhaps cause the problem?

Thanks for your help guys.

---

### Post by aysiu on 2008-02-22
The way to get back to the desktop is typically Control-Alt-F7

If you're stuck at the terminal, sometimes this can help: ```
sudo /etc/init.d/kdm restart
```

---

### Post by danpaquin on 2008-02-22
Thanks for the help, but both running that command as well as <ctrl>+<alt> F7 leaves me with a blinking cursor in the top left of the screen.

---

