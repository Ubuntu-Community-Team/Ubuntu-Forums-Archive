---
title: "Screen Resolution for Dell XPS Laptop"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by Shadow Jolteon on 2008-04-02
My aunt recently tried to set up a secondary monitor for her Dell XPS M1210 notebook. Unfortunately, when she did so and restarted the computer, the settings for the laptop's display had completely changed, making everything appear very large and the external monitor does not work.

I have no idea what to set it to to get it to work again, since when I first installed it, it showed the settings as "custom" and I have no idea how to properly set it for this computer...

Edit: One more thing. Her printer is connected to her router, and she would like to get it set up to work on her Ubuntu machine. How would I go about setting up a network printer?

---

### Post by freed0m on 2008-04-02
For the first problem.

You have to logon on terminal and do:

cd /etc/X11

sudo cp xorg.conf.1 xorg.conf

sudo reboot

Try it and let me know if works.

Cheers.

---

### Post by Shadow Jolteon on 2008-04-02
> **freed0m said:**
> For the first problem.

You have to logon on terminal and do:

cd /etc/X11

sudo cp xorg.conf.1 xorg.conf

sudo reboot

Try it and let me know if works.

Cheers.
Thank you very much, that worked. =)

Now I just need to get that printer to work with the Ubuntu machine...

---

