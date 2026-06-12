---
title: "does nvidia-settings conflict with compiz?"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by mcb01 on 2008-01-23
Hi all, Ubuntu newbie here. I'm trying to get both the Nvidia control panel and compiz to work at the same time. Right now I have compiz installed, which is working ok. Now if I go to a terminal and enter nvidia-settings, it says "you do not appear to be using the nvidia x driver". After some searching, I realized this could be fixed by removing xlg, but then compizconfig stops working. How can I get both to work at once?
Thanks

(and I apologize if the answer has been posted, but I could not find anything that matched this exact situation)

---

### Post by luisromangz on 2008-01-23
If you use the Nvidia driver, you should have no need of using XGl, since it support the composite extension.

There are many howtos explaining the way to enable desktop effects with nvidia drivers, look for them.

---

### Post by mcb01 on 2008-01-24
Thanks, got it working. Here's what I did in case anyone else runs into this:

- uninstalled xgl using sudo apt-get remove --purge xserver-xgl
- went through [**this guide**]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200") until the part where I got to the appearance preferences, because I got a message saying it could not enabled desktop effects
- modified the compiz file using the suggestions in [**this thread**]("http://ubuntuforums.org/showthread.php?t=565186") to allow it to run with 32MB ram since that's what this graphics card has (it's an old laptop)
- ran compiz using alt+f2 and entering compiz --replace

---

### Post by theRightNee on 2008-01-24
i am just putting it out there, does anyone know if Quadro 2 Pro cards work with compiz? i've tried previously, but could not get it working. thanks!

---

