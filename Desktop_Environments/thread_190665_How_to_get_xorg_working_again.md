---
title: "How to get xorg working again"
date: 2006-06-06
forum: Desktop Environments
---

### Post by srunni on 2006-06-06
OK, so I followed the tutorial at [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
in an attempt to get my ATI Radeon X300 card working with Dapper Drake in an XP VMWare installation. When I rebooted, it said that Ubuntu was screwed up and I couldn't get the GUI to load. So now I'm stuck with the good old Linux command prompt. Does anyone know how to fix this through the prompt?

---

### Post by SavageBeginner on 2006-06-06
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by i++ on 2006-06-06
i had the same error with my x800 GTO, i could not start x, as it was using the 'ati' driver. from linux cmd..
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf

```

this will open xorg.conf in nano (if you're familiar with or want to use vi it makes no difference) find the section about your graphics card, and if it says Driver    'ati' change ati to radeon, then ctrl + O to save, and ctrl + x to exit. type 'startx' and this should start your x server

Hope this helps

Edit -- or that ^^

---

### Post by srunni on 2006-06-06
Well, I tried both ideas and neither worked. I couldn't find the graphics card section of my xorg.conf file on the 2nd fix, so that didn't exactly work out. On the first fix, I had to provide a TON of answers to various questions, most of which I didn't know and just went through with the default option. Maybe I will go back later and take a closer look at the options.

---

### Post by arizonagroovejet on 2006-06-06
Try changing the driver to vesa which is like the basic generic driver.

Also, xorg.conf is important. Like any important configuration files you are editing by hand you should make a copy of it before you mess with it. Then if you end up in a mess like you are now you can simply replace xorg.conf with the backup to get back to where you started. I know that doesn't help you right now but bear it in mind for the future.

---

### Post by srunni on 2006-06-06
Yeah, there's a backup of the file in the same directory under the name xorg.conf_backup, so I can just use that. I think the problem is the whole setup, which is automated in the regular installation but for some reason isn't in this xorg setup.

Edit: But guess what? I changed it to vesa, **_AND IT WORKED!!!!!!!!!!!!!!!!!!!!!!_**

But I still haven't got my original problem of wanting Ubuntu to have a 1280x1024 resolution option working. I tried using the 915resolution program or whatever, but it couldn't detect my Intel chipset or something like that. This was probably because I'm running Ubuntu in VMWare, but that's not confirmed.

---

