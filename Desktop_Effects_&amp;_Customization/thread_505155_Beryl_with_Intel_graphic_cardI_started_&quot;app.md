---
title: "Beryl with Intel graphic card

I started &quot;app"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by sunshine12 on 2007-07-19
I have installed beryl, but how to start it..??

I started "applications-system tools-beryl setting manager" but nothing is happening.
also there is no system tray icon

I have intel graphic card, don't know that will run beryl or not..

CARD DETAIL

```
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
```

If somebody can please tell if this will run beryl or not and if yes then how to activate it??

thanks

---

### Post by sunshine12 on 2007-07-20
please someone can help

---

### Post by animeboi252 on 2007-07-20
i have a intel gma 950 and it works on that:o

---

### Post by sunshine12 on 2007-07-20
after installing beryl, it starts automatically or have to do something to activate it??

---

### Post by tekkenlord on 2007-07-20
Have you tried giving from a terminal the command 

beryl-manager

?

This should show you the beryl icon (if it doesn't activate the beryl manager itself). After that you can select the window manager you wish from the icon.

---

### Post by sunshine12 on 2007-07-20
> **tekkenlord said:**
> Have you tried giving from a terminal the command 

beryl-manager

?

This should show you the beryl icon (if it doesn't activate the beryl manager itself). After that you can select the window manager you wish from the icon.

Did that.
After selecting Beryl as the window manager, computer screen turned white.. nothing happened. have to restart....

beryl-manager command also starts some testing things and soon the whole screen becomes white...
what is the actual problem? Is this graphic card run beryl?

thanks for replying.

---

### Post by tekkenlord on 2007-07-20
To check if your video card supports accelerated graphics (therefore probably beryl) issue the following command from a terminal


glxinfo | grep direct

If the output is 

direct rendering: Yes 

then your video card can probably handle Beryl.

Also check your /etc/X11/xorg.conf in the "Module" section if you have the "dri", "vbe", and "glx" modules loaded.

I suggest you also see this link: [https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

---

### Post by sunshine12 on 2007-07-20
Thanks for replying

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


Yes this modules are loaded:  
 /etc/X11/xorg.conf in the "Module" section the "dri", "vbe", and "glx" modules loaded.

Thanks

---

### Post by mysticmatrix on 2007-07-20
As from Beryl's website, minimum card required is i845. Yours is i815 which is tooo old to be supported.

Bottom line: You can't run Beryl with 90% probability.

---

### Post by sunshine12 on 2007-07-20
> **mysticmatrix said:**
> As from Beryl's website, minimum card required is i845. Yours is i815 which is tooo old to be supported.

Bottom line: You can't run Beryl with 90% probability.

Thanks for the information. Removed beryl....

Thanks to all for replying.

---

### Post by animeboi252 on 2007-07-22
> **sunshine12 said:**
> after installing beryl, it starts automatically or have to do something to activate it?? you have to type it in inthe sessions

---

