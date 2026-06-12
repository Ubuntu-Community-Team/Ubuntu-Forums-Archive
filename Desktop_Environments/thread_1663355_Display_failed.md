---
title: "Display failed"
date: 2011-01-09
forum: Desktop Environments
---

### Post by Evandar on 2011-01-09
Hello

I've been trying to revive an old HP Omnibook XE-3 using Ubuntu. After some installation problems, I've finally managed to complete the command line installation on the system. I then proceeded to update the system and install X.org. This is where my problem lies:
everytime I try to use ```
sudo startx
``` to get it running, it fails, no matter what the installed window manager/GUI is. XFCE and LXDE both fail, and even simple WMs like fluxbox fail. Even X.org on its own fails; All of them give me a black screen with which I cannot interact in any way.

Any ideas on what might be causing this? I'll be severely disappointed if it's a hardware issue, since I really want to get that old machine back on its feet. I should mention that I've been experimenting using a virtual machine set up in almost the same manner as the XE-3, and that one runs XFCE (the heaviest one I could possibly use on a less than 256 MB RAM machine) absolutely fine.

---

### Post by jerrrys on 2011-01-09
don't own one, but seems to be a bit in the forum about these old machines

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=HP+Omnibook+XE-3&as_qdr=all&sa=Google+Search&lang=en#1116](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=HP+Omnibook+XE-3&as_qdr=all&sa=Google+Search&lang=en#1116)

---

### Post by Krytarik on 2011-01-09
@jerrrys: The provided URL doesn't work.

I guess jerrrys meant this guide:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

In order to specify the desktop system to load, also look here:
[https://help.ubuntu.com/community/CustomXSession](https://help.ubuntu.com/community/CustomXSession)
[https://wiki.archlinux.org/index.php/Xinitrc#A_standard_.xinitrc](https://wiki.archlinux.org/index.php/Xinitrc#A_standard_.xinitrc)

---

### Post by Evandar on 2011-01-09
Actually, his link worked for me.

As for building a custom session, thanks, I'll try that and see if it works. The only thing is, usually, xorg should not hang the system when used without a specified desktop, which is what worried me.

Edit: the black screen persists... :/

---

### Post by Krytarik on 2011-01-09
> **Evandar said:**
> Actually, his link worked for me.

As for building a custom session, thanks, I'll try that and see if it works. The only thing is, usually, xorg should not hang the system when used without a specified desktop, which is what worried me.

Edit: the black screen persists... :/
How do you specify then which desktop system to load by executing startx, if not with xinitrc or xsession?
It may be that startx tries to load Gnome, which apparently is beyond the power of your machine.

---

### Post by Evandar on 2011-01-09
Well, what I did was I created ~/.xinitrc, linked it to ~/.xsession, and used that. All I typed in the script was ```
exec startxfce4
``` since from what I understood that's all I need to get a basic GUI up. (I also tried it with fluxbox in case xfce4 was too heavy, which it shouldn't be. both failed) I don't really get why it's happening. I also can't locate xorg.conf, which might have helped.

---

### Post by Krytarik on 2011-01-09
I agree to that way.

There is no xorg.conf anymore by default. Maybe you should create one and specify "vesa" as video driver.

---

### Post by Evandar on 2011-01-10
That gave me a massive improvement. Instead of the dead black screen, I now get an error for "No Screens found" - something I can read, at last! The log file said

Vesa:Kernel modesetting driver in use, refusing to load
Falling back to old probe method for vesa
No devices detected

fatal server error:
no screens found.

Google easily came up with a solution to this, but even after using nomodeset, the graphics get screwed up. I've seen this kind of behavior before on laptops with damaged video/graphics chips. Of course, I'm not giving up just yet, so I'll need to try a few different things as well.

Edit: I dunno why I didn't try this. xfce gave screwed up graphics, but that was proof it could at least start. I tried fluxbox instead, and it works. Theoretically, from here on everything should be a piece of cake. Thanks for all the help.

---

### Post by Krytarik on 2011-01-10
Thanks for the feedback. Happy that it works now!

---

