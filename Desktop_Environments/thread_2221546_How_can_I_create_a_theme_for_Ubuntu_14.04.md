---
title: "How can I create a theme for Ubuntu 14.04?"
date: 2014-05-02
forum: Desktop Environments
---

### Post by lads on 2014-05-02
I am slowly upgrading the various systems I work with to Ubuntu 14.04. While I remain an unconditional Unity fan, I find this latest iteration too bright for my eyes. I have tried a number of alternative themes but can't find one that I really like; in great measure because it is now impossible to change the theme and keep the Ambiance window decoration. I think I would should simply create a new theme suiting my liking.

I understand that GTK styles are presently based on CSS, thus creating a new theme should not be theoretically that hard. But so far I have failed to find any information detailing the files needed, and how to installed them. I would just like to start with an exact copy of Ambiance and then start tweaking a few colours. Could anyone explain how to do this?

Thank you.

---

### Post by vasa1 on 2014-05-02
> **lads said:**
> ... I think I would should simply create a new theme suiting my liking.

I understand that GTK styles are presently based on CSS, thus creating a new theme should not be theoretically that hard. But so far I have failed to find any information detailing the files needed, and how to installed them. I would just like to start with an exact copy of Ambiance and then start tweaking a few colours. Could anyone explain how to do this?
...
Starting with an existing theme and tweaking it is easier, IMO. So, provided you have something like Ubuntu Tweak (or whatever), copy the theme you want to modify from /usr/share/themes to ~/.themes and play with the modified version.

GTK3 is CSS-based but GTK2 isn't.

worldofgnome.org/customizing-gtk-themes-just-got-easier/
worldofgnome.org/making-gtk3-themes-part-1-basics/
worldofgnome.org/making-gtk3-themes-part-2-the-gtk-css-and-gtk-widgets-css-files/
worldofgnome.org/making-gtk3-themes-part-3-the-dark-side/

---

### Post by vasa1 on 2014-05-02
By the way, you or someone with the same name had this thread, [12.04: How to change the system background colour?]("http://ubuntuforums.org/showthread.php?t=2041696"), in which [I posted a relatively length response]("http://ubuntuforums.org/showthread.php?t=2041696&p=12171055#post12171055") without any feedback :(

---

