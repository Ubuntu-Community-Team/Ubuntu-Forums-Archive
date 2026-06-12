---
title: "Removing LXDE Components"
date: 2017-09-14
forum: Desktop Environments
---

### Post by Raevyn on 2017-09-14
Hello,

So I wanted to try a pure LXQT environment but I know that Lubuntu 17.04 isnt ready to do that yet, so I did an Ubuntu minimal install but on completion I noticed it still ended up installing the LXDE and LXQT systems. Is there a way to either install LXQT alone or remove the LXDE components specifically in 17.04?

---

### Post by Bucky Ball on 2017-09-14
When you say you did a minimal install, did you [install from the minimal ISO like this]("https://help.ubuntu.com/community/Installation/MinimalCD") and NOT select a machine profile from the tasksel section (for instance, did you choose 'Lubuntu' when asked if you'd like to select a machine profile)?

Try not choosing any machine profile and on first boot, you will be at a login cursor, like a big terminal and not a pretty coloured screen. Login and install lxqt and see how that goes. 

```
sudo apt install lxqt
```

... I would guess. That should also drag in whatever else it needs.

Reboot, login and you should end up at an LXQT desktop minus lxde. (Or is lxde a requirement of lxqt? Not familiar enough with either to know.)

Just a thought.

---

### Post by Raevyn on 2017-09-14
Yes I used the mini iso and went through the console setup where one of the options is specifically LXQT. I just tried selecting that and KDE in the hopes I get at least Kubuntu components (which is fine if I have to) but no, it still throws in LXDE. I will try your way though just in case.

---

### Post by Raevyn on 2017-09-14
Okay I think it did it with your idea. You have to install the minimal disk and choose command line install, let it reboot, then go in and apt-get lxqt openbox xinit   then reboot. Pure minimalist QT beauty right there.

---

### Post by Bucky Ball on 2017-09-15
> **Raevyn said:**
> Okay I think it did it with your idea. You have to install the minimal disk and choose command line install, let it reboot, then go in and apt-get lxqt openbox xinit   then reboot. Pure minimalist QT beauty right there.

Now you got it! That's what I'm talking about. Avoid choosing ANYTHING in the tasksel section (where you chose the lxqt and kde profiles) and let the install go right through (you can just skip tasksel when you get there). 

You will probably find you'll need to add various bits and pieces as you go and it will take awhile before everything is purring along nicely, but worth the effort in my opinion. When you get it there, make a backup of it before going too much further. You can create an ISO of your current install. Handy as means you don't need to work it up again next time (some users have come up with scripts and other things to automate the process, but I never got that far).

Enjoy! ;)

(PS: If you're happy, please mark the thread as solved from Thread Tools at top right to help others. This does not close the thread to further discussion.)

---

