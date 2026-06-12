---
title: "Major problems"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Dazza on 2006-07-18
I have been running Dapper for around 2 hours, had my nvidia drivers installed etc. Rebooted a couple of times, usual computer usage. I tried to use the Mouse hack to get all buttons on my Mx510 to work, but when I went to restart the xserver (control alt backspace) I was presented with a white screen and a massive nvidia logo.

How do I fix this? I got no idea what has happened, i'm assuming graphics drivers, but they were working perfectly before the install of the mouse drivers...

Thanks for any help. :rolleyes:

---

### Post by ohgod on 2006-07-18
Do you mean that the nvidia logo doesn't go away?  When you use the binary nvidia drivers that screen pops up for a moment before you get the login screen...

---

### Post by Dazza on 2006-07-18
Yeah, the white screen comes up and jack shit happens, i've left it open for like 10/20 minutes and nothing.

What i did to try and fix it:

sudo nano the xorg.conf file:::

I changed nvidia to nv (like a guide I read said), now when I boot the OS, I get basically a terminal window and I don't know where to go from here, I can't boot into the white logo screen anymore either.

Edit: I assume I need to run gnome, correct?

---

### Post by Dazza on 2006-07-18
Please help i'm crying here :(

---

### Post by TheMindField on 2006-07-18
The best bet in this case to change your driver back from "nv" to the default nvidia driver in /etc/X11/xorg.conf.

You can do this by going into safe mode, waiting for it to load, and then at the terminal type "sudo nano /etc/X11/xorg.conf"

Enter your password, then change it back.

Having a screen and working graphics card is alot better than having extra buttons on a mouse work.

I suggest you find a different guide for the mouse thing, and see if you get a different result.

---

### Post by Dazza on 2006-07-18
Thing is, I changed it FROM nVidia to nV, as before it just hung at the white screen.

---

### Post by brownrl on 2006-07-18
Isn't there a command to redo the xorg.conf file?

something like?

sudo dpkg --configure yada yada yada

its mentioned in the top of the xorg.conf file hold on...

got it:  

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you your default xorg conf file back and should get you in the game again.

As for you mouse, I got the MX1000 I don't have the side ways buttons working ( really needed? ). I do however have the back and forth handy buttons working for the browser using a xbindkeys trick which I am sure you have seen.


.xbindkeysrc file
```

"xvkbd -no-repeat -xsendevent -text "\[Alt_L]\[Left]""
   m:0x10 + b:8 + Release
"xvkbd -no-repeat -xsendevent -text "\[Alt_L]\[Right]""
   m:0x10 + b:9 + Release

```~


Then run xbindkeys when you login...

---

### Post by Dazza on 2006-07-18
Okay, I fixed Ubuntu and I am now posting from it. It was just because of my stupidity, but it is now fully functioning. I restored my xconf file and then set my resolution etc and I am set to go, again. lol.

Any idea how to make the scroll wheel scroll faster, lol?

---

