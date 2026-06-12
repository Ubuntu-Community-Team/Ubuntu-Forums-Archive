---
title: "menu (button) slow"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by HavanA on 2007-05-21
I use Ubuntu on my laptop, for internet only. At home I use Ubuntu Ultimate and at both computers I have replaced the "applications-places-system"-menu for a small menu button. Each time I want to open the menu for the first time, it takes about just a little less than 10 seconds to open. From then it opens immediately when used. 

I have no heavy software running in the background and this happens with both computers. I noticed that  on the system monitor, gnome-panel is using lot of the processor power when I click this button for the first time. I have given this proces a top priority but it does not help.

Any thoughts?


Thanks,
Glenn form The Netherlands

---

### Post by whayong on 2007-05-21
Yes, I get the same.  This only happens the first time you click on the menu, after that, all is well.  I always thought it could be my hardware.  It might help if you post your hardware specs.

---

### Post by orb9220 on 2007-05-21
This is normal and there is a setting to make it instant on first click.

I to also trying to find and remember I did it last year. It is just a setting and is in these forums somewhere.

I will be tracking this down and will post here when I find it.
If you find it post here for others.

Found!

[http://ubuntuforums.org/showthread.php?t=215119](http://ubuntuforums.org/showthread.php?t=215119)

Works just open gedit and add **gtk-menu-popup-delay = 0** and save as **.gtkrc-2.0** in your home/user whatever folder and log out and log back in.

---

### Post by HavanA on 2007-05-22
thanks for your comments. Indeed the button is delayed only the first time I click. I have created the file as described in the link provided, but it does not work on the button itself. It does however make the changing within the menu fast (e.g. when you point at "internet" and then point at "office", the menu will show immdiately and is not delayed anymore). I like that. Thanks!

Maybe there is also a solution to make the menu button itself popup faster (the first time you click it). If I am not mistaken, the original menu of Ubuntu is not delayed when clicked for the first time?

---

### Post by hayalci on 2007-05-27
The link provided by orb9220 has a solution for your problem also.

You should run the following commands on system startup
find /usr/share/pixmaps/ | xargs cat > /dev/null
find /usr/share/icons/Human/ | xargs cat > /dev/null

---

