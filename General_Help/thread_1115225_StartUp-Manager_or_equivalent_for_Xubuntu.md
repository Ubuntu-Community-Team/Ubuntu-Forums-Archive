---
title: "StartUp-Manager or equivalent for Xubuntu"
date: 2009-04-03
forum: General Help
---

### Post by yosumi on 2009-04-03
Before getting Xubuntu 9.04, I want to know if it supports this program called StartUp-Manager. 

It's the first thing I download right after installing Ubuntu. It helps me get rid of the orange progress bar on boot and shut down. I am sure Xubuntu's progress bar looks even worst. Personally, I like text verbose with high resolution. :p

---

### Post by ibuclaw on 2009-04-03
Startup-Manager may work in Jaunty, but you will have to find that out yourself by trying it out.

If it doesn't there are other ways to remove usplash and setup the console text.

First, though, make a backup of your boot list.
```
sudo cp /boot/grub/menu.list /boot/grub/menu.lst.backup
```
Then edit
```
sudo gedit /boot/grub/menu.lst
```
Locate the following line:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet splash**

```
And remove the word **splash**.

As for setting up the console text, you use the option **vga**.
If you know what resolution to use, then put it in on the same line you just edited:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet **vga=791**

```

If you are unsure, just put in **vga=ASK** and you'll be prompted when you next reboot. Then you can later re-edit the menu.lst file once you know for sure which text resolution you want.

To apply the settings you just made:
```
sudo update-grub
```

Regards
Iain

---

### Post by yosumi on 2009-04-03
Thank you so much. Editing menu.lst is something I want to try. If my laptop's resolution is 1024x786, the code line will be "# defoptions=quiet vga=786"??

---

