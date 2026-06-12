---
title: "Mouse Pointer / cursor with compiz fusion"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by bss on 2007-11-22
I have a problem with some other cursor / mouse pointer theme. When I go to appearance and change the mouse pointer, the new theme only works in windows that are not from system. Ex: when i change my cursor theme from default to white glass, I can only see the new theme in firefox window and on plain desktop, but when I move my mouse to gnome menue (upper left corner of screen) the cursor changes back to default or when i move my mouse to any configuration windows (eg.: appearance window,...). When not running compiz fusion it works fine, it only causes trouble when running compiz fusion. Apart from that I have never had any troubles with Compiz-fusion.

Have a nice day and happy posting :)!!!

bss

---

### Post by Forlong on 2007-11-22
Install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Run it via *System &#8594; Preferences &#8594; Advanced Desktop Effects Settings*
Then go to **General Options &#8594; Cursor theme** and change
```
default
``` to ```
whiteglass
```

---

### Post by bss on 2007-11-23
Cool it worked, partly.
Can you tell me how to change size of pointer form compiz config?

---

### Post by bigfork181 on 2007-12-17
What do you change default to in order to use DMZ (Black)?

Edit: I figured it out, I changed it to "DMZ-Black".

---

### Post by westbywest on 2007-12-27
Accidentally posted to wrong thread.  Please disregard this reply.

---

### Post by b0rka7a on 2007-12-28
It worked, but in Firefox the cursor is the default :(
Damn! :)
Any idea how to change it?

---

### Post by bss on 2007-12-28
Have you changed the cursor theme in System -> Settings -> aperance -> theme -> pointer???
I don't know but on some programs it uses the system (aperance setting) cursor theme, on the other programs it uses the compiz's.

try doing it so and tell me if you suceed.

Good luck!

---

### Post by FuturePilot on 2007-12-28
> **b0rka7a said:**
> It worked, but in Firefox the cursor is the default :(
Damn! :)
Any idea how to change it?

Try going into CCSM under the General section and hit the Reset button next to the Cursor theme line.

---

### Post by b0rka7a on 2007-12-28
> **bss said:**
> Have you changed the cursor theme in System -> Settings -> aperance -> theme -> pointer???
I don't know but on some programs it uses the system (aperance setting) cursor theme, on the other programs it uses the compiz's.

try doing it so and tell me if you suceed.

Good luck!

It worked great! Thanks!
But I have another issue :).
(I don't know exactly how to say it, because I'm good at English, but I'll try...)
When my cursor is on one of the corners of the window (not resizing) is in the Ubuntu default theme, but when I start resizing the window it changes to my custom cursor theme. I hope you can tell me how to fix this.

P.S: It's not that important, but I want to be perfect :P
P.S.2: Because I don't know how to make a screenshot which includes the mouse cursor, I didn't attach nothing.

Edit: Not only on the corners, but on the top and bottom lines for resizing too

---

### Post by Forlong on 2007-12-29
Are you using Emerald?

---

### Post by b0rka7a on 2007-12-29
Everything is working wonderful now! :D
Yes, I'm using Emerald, but today after I restarted my PC it was fixed. I think it just needed to reboot (or just to restart the X server), because I didn't change anything before I restarted the PC.
Thank you for the help and Happy New Year!

---

### Post by bss on 2007-12-29
> **b0rka7a said:**
> Everything is working wonderful now! :D
Yes, I'm using Emerald, but today after I restarted my PC it was fixed. I think it just needed to reboot (or just to restart the X server), because I didn't change anything before I restarted the PC.
Thank you for the help and Happy New Year!

Yep that's a common fix of problems :-D I'm glad it worked out for you.

Also Happy New Year (and as Christmas has alredy been, I wont say Mery Christmas. but I hope you did enjoy your christmas) to all of Ubuntu users (or any other Linux distro. users or supporters) and of course Ubuntufrums.org staff and users!!!):P

---

