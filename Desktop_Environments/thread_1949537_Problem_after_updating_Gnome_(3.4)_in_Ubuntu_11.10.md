---
title: "Problem after updating Gnome (3.4) in Ubuntu 11.10"
date: 2012-03-30
forum: Desktop Environments
---

### Post by Pescador12 on 2012-03-30
Hi all,

I am using gnome shell for a while, and loving it, but with some minor bugs, so I've tryed to upgrade to the new gnome 3.4, and now in the login screen my icons disappeared, and when I try to login, a black screen appears with my mouse cursor and nothing else. So there's nothing I can do!! 

I've already tryied to login in another desktop enviroment (Ubuntu classic, Ubuntu 2D, etc) but the same happens!!

By the way, when upgrading, one package gave an error, but I don't remember which.

Any help?

---

### Post by Frogs Hair on 2012-03-30
How did you attempt the upgrade ? I have only found a PPA for 3.4 on 11.10 . The  Gnome Shell 3.4  will be included with 12.04 .

---

### Post by Pescador12 on 2012-03-30
> **Frogs Hair said:**
> How did you attempt the upgrade ? I have only found a PPA for 3.4 on 11.10 . The  Gnome Shell 3.4  will be included with 12.04 .

I've just followed this instructions:
> sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

---

### Post by Frogs Hair on 2012-03-30
That would be a PPA  and there is always risk when using a PPA because they are they are unofficial .
The message at the l link is clear make sure you know what you are doing because the PPA may break your system. [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

It is also  stated  to enable proposed updates prior to using the PPA . I don't know if you had done this and if not you may be missing required packages .  That was written quite a while ago and there is nothing to indicate that  it no longer applies .

I don't know how to repair this problem , so you will have to wait to get help from another member . Remember to backup your files before using any bleeding edge applications .

---

### Post by Pescador12 on 2012-03-30
SOLVED!

Like you said, there were problems with dependencies, so I had to "apt-get -f install", and that's it!

Thanks

---

