---
title: "GDM greeter customisation"
date: 2020-05-04
forum: Desktop Environments
---

### Post by pablosquared on 2020-05-04
One of the things I do with a new version of Ubuntu is customise the login greeter background. In the past on this system, that's involved editing the gdm3.css style sheet to point to an image of my choosing. However, in 20.04, the gdm3.css sheet doesn't exist so I can't point it to my preferred image file.

```

pablo@Ubuntu:~$ locate gdm3.css
pablo@Ubuntu:~$ 

```

So, how can I configure the background of the login greeter? I had a look round dconf-editor, including org/gnome/login-screen without success.

TIA!
PP

---

### Post by tea for one on 2020-08-28
There is a script which can be used to change the background on the gdm3 log in screen (Ubuntu 20.04 only)

It was mentioned in post no. 9 of a recent thread. [https://ubuntuforums.org/showthread.php?t=2449488](https://ubuntuforums.org/showthread.php?t=2449488)

[https://github.com/thiggy01/ubuntu-20.04-change-gdm-background](https://github.com/thiggy01/ubuntu-20.04-change-gdm-background)

I have had a play with it and it's pretty good.

---

