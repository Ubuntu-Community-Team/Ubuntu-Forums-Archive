---
title: "Brightness"
date: 2005-06-24
forum: Desktop Environments
---

### Post by rathel on 2005-06-24
I'm nost sure if this is the right category or not. Ubuntu Detected all my hardware on my Vaio Laptop just fine, but my problem is that my screen isn't bright enough, how do I adjust the brightness? In windows all I do is hit Fn+F6 but on linux I have no Idea what to do. Any help would be great. Thanks.

---

### Post by elvis on 2005-06-24
Open a terminal, and edit your xorg.conf file:

```

sudo nano -w /etc/X11/xorg.conf

```

(inside of nano, CONTROL+X exits and prompts to save the document)

Where it says 'Section "Monitor"' add in there somewhere the line "Gamma 1.3".  For instance, in my xorg.conf file I have:

```

Section "Monitor"
   Identifier                   "monitor0"
   HorizSync                    30 - 120
   VertRefresh                  60 - 85
   Option                       "dpms"
   Gamma                        1.4
EndSection

```

You can increase or decrease your gamma settings here.  The default is "1.0".  My monitor is quite old and dark, and I find 1.4 suits me well.  Experiment with yours to find what works best for you.  Valid numbers are 0.1 to 10.0.

If you specify a single number, it will apply evenly to all channels (red, green and blue).  Optionally, you can specify three different numbers (eg: "Gamma 1.0 1.0 2.0") if you want to change the Gamma of each channel separately.  This is handy if you have an older CRT monitor that might be starting to colour shift a little.  Laptop/LCD/TFT users probably don't need to bother.

Each time you change this setting, you need to restart X.  The easiest way is to log out of your desktop (back to the login screen) and press CONTROL+ALT+BACKSPACE (not DELETE!) which will shut down X, and the Ubuntu scripts will start it back up again with the new Gamma applied.

You can apply different Gamma settings per monitor if you are using multiple monitors.

---

### Post by rathel on 2005-06-24
Okay, i just got done trying that, and it seems to make the White brightner and not the actual monitor, i don't have a physical button to make it bright... so what now?

---

### Post by elvis on 2005-06-24
Ah, I understand now.  The Vaio's rely on software to understand their key shortcuts.  Very poor design there, Sony.

There's a good guide here:

[http://wiki.unixgate.ch/index.php/Gentoo_on_Sony_Vaio_TR5MP](http://wiki.unixgate.ch/index.php/Gentoo_on_Sony_Vaio_TR5MP)

To get the sony brightness keys working on Gentoo.  Most of it should work under Ubuntu, as both use a 2.6 kernel and Xorg.

Hope that helps.

---

### Post by rathel on 2005-06-24
Hey thanks! I'll give it a shot.

EDIT: That's kind of confusing since I'm not using Gentoo, I wish there was some easy to understand how-to for doing this.. hmm..

---

### Post by rathel on 2005-06-25
Great Site: [http://www.shinelife.co.uk/ubuntu-vaio-pcg-v505cp/backlight.php](http://www.shinelife.co.uk/ubuntu-vaio-pcg-v505cp/backlight.php)
But I still got a problem.. Whenever I try to increase the brightness I get this:

```
rathel@ubuntu:~$ sudo spicctrl -b 255
/dev/sonypi: No such file or directory
```

---

### Post by bored2k on 2005-06-25
> Please do not post questions here. This is for HOWTO's and FAQs only..

---

### Post by rathel on 2005-06-25
Oh oops, mah bad.

---

