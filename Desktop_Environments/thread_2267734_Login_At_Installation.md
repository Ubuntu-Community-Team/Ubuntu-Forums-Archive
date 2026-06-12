---
title: "Login At Installation?"
date: 2015-03-03
forum: Desktop Environments
---

### Post by Jokubas_Matonis_LT on 2015-03-03
Hi Guys Iim Got Ubuntu Stick And My USB Stick Is Working Fine But When I Install Ubuntu It Asks Login To Get To Setup[ATTACH=CONFIG]260424[/ATTACH].Please Help To Log In So I Can Contuine My Ubuntu Installation. :(

---

### Post by v3.xx on 2015-03-03
Well, it didn't work.

Did you try it out before installing?  And what did you install?

What are your computer specs (ram, cpu, video)?

Edit: My bad ..

You installed 12.10, it has reached EOL.

---

### Post by buzzingrobot on 2015-03-03
Something -- impossible to say what given the brevity of your post -- is wrong with either the installation image you've burned to the USB stick or the way it was burned. The standard Ubuntu install ISO image boots to a graphical screen offering a choice to "Try Ubuntu" in live mode or to install Ubuntu. That's what you should see.

---

### Post by grahammechanical on 2015-03-03
Ubuntu runs on top of LInux. So, when the operating system first starts to load it is Linux that is loaded first. Then at some point Ubuntu has to load on top of Linux and that is when Ubuntu logs in to Linux in our name using the password that we set during the installation. Normally this happens so fast that we may not notice it. In your case the OS loading process seems to be stopping at the point where Linux is running and it gets no further.

As already stated this should not happen during the installation of Ubuntu. The fact that it is happening makes me wonder if you have installed Ubuntu 12.10 to the USB stick instead of creating a USB Ubuntu installer. I am even wondering if this is a Ubuntu server edition.

Regards.

---

