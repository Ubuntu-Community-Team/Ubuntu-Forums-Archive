---
title: "nVidia and Beryl lost settings after reboot."
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by xeo_pt on 2007-07-15
Hi,
I have a nVidia and a Apple Cinema 22" and just install ubuntu 7.04 with beryl.
It works great!

My problem is that after a reboot Gnome returns to to 800x600 and I have to run nVidia settings
to set up everything again (the Beryl settings).
Why does Gnome "forgets" the resolution settings.

Any help will be great.

Thanks in advance.

---

### Post by linuxwizard on 2007-07-15
15) If "nvidia-settings" loses its settings every time you reboot Get to the following menus (if you use GNOME): System -> Preferences -> Sessions -> Startup Programs

Then click on "Add"

And insert this command:

nvidia-settings --load-config-only

Then click on "Close". 


Quoted from here at bottom of page
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28CategoryDocumentation%29#head-4361d5838b8fe73fad05dcad1ee95ddbeabca7c5](https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28CategoryDocumentation%29#head-4361d5838b8fe73fad05dcad1ee95ddbeabca7c5)

---

### Post by xeo_pt on 2007-07-17
No, it doesn't work and now I have more problems.

Thanks anyway.

---

