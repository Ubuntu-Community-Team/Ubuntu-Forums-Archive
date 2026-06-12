---
title: "Xubuntu HELP!"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Chiaro on 2005-12-10
I just installed Xubuntu via server install around 3 hours ago. So Xubuntu boots up, it looks good, and I notice the screen resolution is too low(640x480). So I click 800x600, and I see 7 lines for a desktop and a white line for my mouse. The screen is so messed up I can't change it back. HELP!

---

### Post by aysiu on 2005-12-10
Any luck with Control-Alt-Backspace or Control-Alt-F1?

---

### Post by Jason-X on 2005-12-11
I had the same trouble with Xorg when doing a server install. When I did the full install with the gnome desktop it configures Xorg perfectly, but with a server install it did not. 

If you can logout or restart and get to the command prompt (Control-Alt-Backspace should work) before you startx you can run:

> sudo dpkg-reconfigure xserver-xorg

and go through the setup screens. This worked for me. You will be able to enable the screen resolutions that you want and the colour depths etc. I also made a backup copy of my /etc/X11/xorg.conf file when I did a full install. This was handy to refer to.

Hope this helps.

---

### Post by Chiaro on 2005-12-11
[QUOTE=aysiu]Any luck with Control-Alt-Backspace or Control-Alt-F1?[/QUOTE]

The first one brought me back to the GDM login screen, the 2nd one brought me all the way back to the server where I couldn't load GDM...

[QUOTE=JasonX]
I had the same trouble with Xorg when doing a server install. When I did the full install with the gnome desktop it configures Xorg perfectly, but with a server install it did not. 

If you can logout or restart and get to the command prompt (Control-Alt-Backspace should work) before you startx you can run:


Quote:
sudo dpkg-reconfigure xserver-xorg  


and go through the setup screens. This worked for me. You will be able to enable the screen resolutions that you want and the colour depths etc. I also made a backup copy of my /etc/X11/xorg.conf file when I did a full install. This was handy to refer to.

Hope this helps.[/QUOTE]

But it only messed up when I changed the resolutions on the Xubuntu GUI...

---

### Post by rejser on 2005-12-11
ctrl+alt + "+ or -"
changes resolution up and down while x-server is started
Know it aint the answer to your question, but if you end up in a screwy situation you can try this.

---

### Post by aysiu on 2005-12-11
[QUOTE=Chiaro]The first one brought me back to the GDM login screen, the 2nd one brought me all the way back to the server where I couldn't load GDM...[/quote] Okay. Do control-alt-F1 and type ```
sudo dpkg-reconfigure xserver-xorg
```

---

