---
title: "quick question"
date: 2009-02-07
forum: General Help
---

### Post by Trim0 on 2009-02-07
I hope this doesn't sound too odd but I'll try my best.
In ubuntu 8.04 if you went to "system, preferences" the menu had an option regarding graphics and resolution. that option is missing in ubuntu 8.10, however, i know that it can be accessed through the terminal, and if i access that option, i will be able to active my nvidia card. does anyone have the code? i'm sorry that i don't remember what exactly that option was but if i remember correctly it was something like "graphics and other" or something like that, all i know is that option was in 8.04 but not in 8.10.

someone help please...

---

### Post by photon_man62 on 2009-02-07
> **Trim0 said:**
> I hope this doesn't sound too odd but I'll try my best.
In ubuntu 8.04 if you went to "system, preferences" the menu had an option regarding graphics and resolution. that option is missing in ubuntu 8.10, however, i know that it can be accessed through the terminal, and if i access that option, i will be able to active my nvidia card. does anyone have the code? i'm sorry that i don't remember what exactly that option was but if i remember correctly it was something like "graphics and other" or something like that, all i know is that option was in 8.04 but not in 8.10.

someone help please...

System>Preferences>Screen Resolution

To activate the graphics card
System>Administration>Hardware Drivers

No idea about the terminal, though.

---

### Post by paydaydaddy on 2009-02-07
Maybe what you are looking for is under system > Administration > hardware drivers.

---

### Post by howefield on 2009-02-07
> **Trim0 said:**
> In ubuntu 8.04 if you went to "system, preferences" the menu had an option regarding graphics and resolution. that option is missing in ubuntu 8.10,..

Does system > preferences > Screen Resolution  give you what you need ?

---

### Post by Trim0 on 2009-02-07
> **howefield said:**
> Does system > preferences > Screen Resolution  give you what you need ?

no that's not it, there was an option in the preferences menu in 8.04 that isn't in 8.10. if i access that option through the terminal, i can active nvidia, otherwise for some reason it won't allow me to activate it because apparently the license is proprietary or something like that.

---

### Post by Trim0 on 2009-02-07
> **paydaydaddy said:**
> Maybe what you are looking for is under system > Administration > hardware drivers.

i'm trying to active nvidia so i can change my hideous resolution, i'm stuck at 800x600 and it won't allow me to active

---

### Post by Trim0 on 2009-02-07
*update guys*
i just finished downloading and installing some updates, but some of them were unsuccessful. now i'm getting "broken package" errors and some of my software is just crashing! i don't know what's going on, all i'm trying to do is activate nvidia, can anybody help?

---

### Post by paydaydaddy on 2009-02-07
So, did you go to system > administration > hardware drivers? I have the option to change graphics card drivers when I go there. Once you have the right drivers, follow this guide. It worked for me.

First make sure that you are using the best drivers for your graphics card, then follow this guide.

I Installed my graphics card driver, but I still can't get the proper screen resolution! What do I need to do?

Sometimes you will need to configure the X Server. It often can't display any larger than 1024 x 768. Here is a quick way to do so. Note: You will need to be logged in as a root user.

1. Open up a shell terminal session
2. Type in the following command:
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

3. Enter your password at the prompt. You will notice it won't actually show up on the screen, this is normal.
4. You will now be shown a GUI. Select your graphics chipset. If you don't know, use Everest and go to Display > GPU. Press enter to continue.
5. Now select the resolution of your monitor. You can select as many as you need. Use the space bar to put an asterisk next to a resolution.
6. Once you are back to the terminal, exit out of the session and reboot to restart the X Server. It should now display the correct resolution.

---

### Post by paydaydaddy on 2009-02-07
Open synaptic and under edit click "fix broken packages". Then check for upgrades.

---

