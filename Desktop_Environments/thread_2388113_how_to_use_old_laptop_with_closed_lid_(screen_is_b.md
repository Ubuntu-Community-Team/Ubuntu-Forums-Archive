---
title: "how to use old laptop with closed lid (screen is broken)"
date: 2018-03-28
forum: Desktop Environments
---

### Post by matrooswolf on 2018-03-28
Hi,

I have an old laptop with a broken screen. I recently installed Ubuntu 17.10. I have attached a screen (vga) and a wireless keyboard and mouse and everything works fine.

I would like to use the laptop with the screen closed (it is broken anyway), but when I close the lid, the vga screen goes black. I suppose the laptop goes in suspend mode. But I turned suspend off (in gnome-tweaks energy suspend when close lid).

I also read somewhere that you could turn off the screen completely, but I don't see a button to that effect in settings/screens. I can see both screens, choose the vga as my primary screen, but I cannot disable the build in screen...

Anybody any suggestions how I could use the laptop with the lid closed?

[does anybody know how to move this thread to general help, because I posted it in the wrong forum, I believe...]

---

### Post by yancek on 2018-03-28
Have you tried the steps at the Ubuntu site below, System Settings, Display.

[https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html](https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html)

---

### Post by matrooswolf on 2018-03-28
Hi Yancek,

I have looked at that, but when I open System setting, Display, there is no turn of button for the screen. Only, orientation, resolution, refreshrate and nightlight. That's all. No way to turn the broken monitor off.

And even then, wouldn't closing the lid still bring the computer in suspend mode? How do I turn that off? To be clear: in gnome tweaks suspend when closing lid is OFF.

[does anybody know how to move this thread to general help, because I posted it in the wrong forum, I believe...]

---

### Post by kerry_s on 2018-03-28
>  I have looked at that, but when I open System setting, Display, there is no turn of button for the screen. Only, orientation, resolution, refreshrate and nightlight. That's all. No way to turn the broken monitor off.
there should be a make primary.

>  And even then, wouldn't closing the lid still bring the computer in suspend mode? How do I turn that off? To be clear: in gnome tweaks suspend when closing lid is OFF.
settings-> power

if it needs to be moved, the admins will take care of it.

---

### Post by matrooswolf on 2018-03-29
HI kerry_s,

There is indeed a make primary, and I made the vga screen primary. But that doens't solve the problem of turning off the broken build in screen. There is no button for that.

And I turned off suspend in settings -> power (as I already stated in my first post) but to no effect. When I close the lid, the vga screen (primary screen) goes blank. Result: I cannot use the laptop with the lid closed...

[is there an admin who can move this thread to general help, because I posted it in the wrong forum, I believe...]

---

### Post by kerry_s on 2018-03-29
sorry, i don't have a vga to test.
i connect mine by hdmi, select single display. i closed the laptop & it stayed up there. looks like this:
[ATTACH=CONFIG]279131[/ATTACH]

normally, there is a setting in the bios, but if your display is broke i assume you can't read the bios.

---

### Post by sandman887 on 2018-04-02
In mate's power management, if you're using the menu with Applications Places System (custom menu? IDR) If you go System > Preferences > Hardware > Power Management, under Actions, there's a place asking what to do if the laptop lid is closed. On the laptops I have that I've turned into servers, I always leave them closed, since there's no reason to use up power for the screen, so I chose "Do nothing". So then when you close the lid, nothing will happen, and your laptop will act like a "desktop" then.

---

