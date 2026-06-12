---
title: "[HELP] GXMame &amp; USB game pads"
date: 2010-05-05
forum: Gaming &amp; Leisure
---

### Post by WarrenSH on 2010-05-05
[FONT=Arial][SIZE=2][COLOR=Black]I was able to install & load ROMs using **GXMame**. I used this tutorial to install **GXMame** [COLOR=Navy][http://www.danielandrade.net/2008/01/08/running-mame-games-on-ubuntu/](http://www.danielandrade.net/2008/01/08/running-mame-games-on-ubuntu/)[/COLOR]

I am having problems with getting my USB game pads to work. I have 2 different type of USB game pads. 

[/COLOR][/SIZE][/FONT][FONT=Arial][B][SIZE=2][I][COLOR=Black]Logitech Dual Action Pad
[/COLOR][/I][/SIZE][/B]_[SIZE=2][COLOR=Navy]*[http://www.newegg.com/product/product.aspx?item=N82E16826127204](http://www.newegg.com/product/product.aspx?item=N82E16826127204)*[/COLOR][/SIZE]_[B][SIZE=2][I][COLOR=Black]

Gravis GamePad Pro
[/COLOR][/I][/SIZE][/B]_[SIZE=2][COLOR=Navy]*[http://www.amazon.com/Kensington-Gravis-Gamepad-Pro-USB/dp/B00000K4TQ](http://www.amazon.com/Kensington-Gravis-Gamepad-Pro-USB/dp/B00000K4TQ)*[/COLOR][/SIZE]_[B][SIZE=2][I][COLOR=Black]
[/COLOR][/I][/SIZE][/B][/FONT][FONT=Arial][SIZE=3]

Can someone please help me with getting the USB game pads to work please. Maybe someone can make a *screen-shoot tutorial/how t*o for me/us all that might be having the same problems.

Thank you in advance.  
[/SIZE][/FONT]

---

### Post by darkforester67 on 2010-05-05
Did you try installing any drivers for thoso two joysticks?
If there isn't for linux try installing the logitech dual action one by using wine

---

### Post by WarrenSH on 2010-05-06
> **darkforester67 said:**
> Did you try installing any drivers for thoso two joysticks?
If there isn't for linux try installing the logitech dual action one by using wine


I do not know how wine would make this work for me when it comes to the drivers. Does anyone ells have any ideas on how I can get MAME to work on ubuntu 9.10 & use one of my two USB game pads?

---

### Post by WarrenSH on 2010-05-07
bump bump bump

---

### Post by WarrenSH on 2010-05-17
> **WarrenSH said:**
> bump bump bump


Still seeking help :P

---

### Post by hikaricore on 2010-05-17
Check the output of **dmesg** from a terminal after plugging in your devices to see if they're recognized.
More than likely your pads work without any kind of configuation or drivers, it's uncommon for hardware of this nature not to these days.
I'm also assuming you're using sdlmame along with the gxmame frontend?
Just open up the sdlmame config screen (can't remember off the top of my head how) while it's running and configure your joysticks there.
You may need to check the manpages or search around to find out what keys do what in sdlmame, I'm thinking it's tab or ~ but it's been awhile since I've messed with it.

---

### Post by WarrenSH on 2010-05-17
> **hikaricore said:**
> Check the output of **dmesg** from a terminal after plugging in your devices to see if they're recognized.
More than likely your pads work without any kind of configuation or drivers, it's uncommon for hardware of this nature not to these days.
I'm also assuming you're using sdlmame along with the gxmame frontend?
Just open up the sdlmame config screen (can't remember off the top of my head how) while it's running and configure your joysticks there.
You may need to check the manpages or search around to find out what keys do what in sdlmame, I'm thinking it's tab or ~ but it's been awhile since I've messed with it.


I use the tab key to open the mapping for the mame emu. I am running kxmame it read my roms better & plays more then the gxmame. 

When I go to map out my d pad nothing reads I get a blank option to pick from :(

---

### Post by hikaricore on 2010-05-17
They're both just frontends and should not differ in any respect, as I said check that your devices are being properly recognized and go from there.

---

