---
title: "Screen Resolution"
date: 2008-10-24
forum: Desktop Environments
---

### Post by wyrfxrssn on 2008-10-24
I'm new to Ubuntu, and my graphics card isn't compatible with it. I have Ubuntu 8.04. I wanted effects on my computer, so whenever I enabled my graphics card to use them everything started looking messed, but when it wasn't enable they were fine. Then my friend who knows more about it downloaded something to try and fix the messed-up-ness. It did not work. And now, when the graphics card isn't enabled, my biggest screen resolution is 800x600. Help?

---

### Post by overdrank on 2008-10-25
> **wyrfxrssn said:**
> I'm new to Ubuntu, and my graphics card isn't compatible with it. I have Ubuntu 8.04. I wanted effects on my computer, so whenever I enabled my graphics card to use them everything started looking messed, but when it wasn't enable they were fine. Then my friend who knows more about it downloaded something to try and fix the messed-up-ness. It did not work. And now, when the graphics card isn't enabled, my biggest screen resolution is 800x600. Help?

Hi and welcome, you can try and boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics.
What is the model of the graphics card?

---

### Post by wyrfxrssn on 2008-10-28
IT just says NVidia accelerated graphics driver in hardware drivers.

---

### Post by tuxxy on 2008-10-28
Follow overdranks advice and fix the issue first, you could also reconfigure the xorg from terminal using the following command

```
sudo dpkg-reconfigure xserver-xorg
```

Now another option once back to normal is download envyng-gtk from the repos and see if this is any better at installing the correct drivers.

```
sudo apt-get install envyng-gtk
```

It would be very helpful to know your nvidia card model, you could navigate to **applications > system tools > sys info > nvidia** which should display the model

---

### Post by suncoolsu on 2008-10-29
I am also new to ubuntu. Can you please tell how to check which video card is detected by the OS? Which drivers have been installed and whats the resolution ?

Thanks

---

### Post by overdrank on 2008-10-29
> **suncoolsu said:**
> I am also new to ubuntu. Can you please tell how to check which video card is detected by the OS? Which drivers have been installed and whats the resolution ?

Thanks

Hi and you can use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
``` It will identify your card and drivers that is detected and used by Ubuntu. You can use the command lspci in the terminal to identify your hardware and look for VGA that is the graphics card.

---

### Post by suncoolsu on 2008-10-29
I did that. When I go to the Graphics Card tab and change my VGA to Intel and select the appropriate Model no which is 965 - I get an error when I test it - saying that it failed to load the drivers. 

Also in the screen tab if try changing the screen type from "plug and go" to Dell with max resolution 1280 x 800 (WGA) again there is an error when I test it saying - it failed to load the screen resolution.

Is it because of my Intel GMA X3100 VGA Card? - Because my readings on google and this formum point towards the same?

If yes - is there a solution?

Thanks
B.

---

### Post by icodeme on 2008-10-29
Easy steps.. 

1.) Reboot
2.) Press "esc" to proceed to menu
3.) Choose the last option.. Not so sure but I think it has something like " Fix Xserver "

Then it'll autodetect and things will get smooth.:popcorn:

---

