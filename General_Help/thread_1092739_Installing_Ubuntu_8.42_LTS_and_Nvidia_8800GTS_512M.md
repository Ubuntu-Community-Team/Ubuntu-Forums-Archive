---
title: "Installing Ubuntu 8.42 LTS and Nvidia 8800GTS 512MN ?s."
date: 2009-03-10
forum: General Help
---

### Post by Alazahr on 2009-03-10
Greetings my fellow Linux users.

I have to say a coworker suggested I get into Ubuntu after showing my interest in Linux and I am highly pleased w/ it so far. I do have a few questions though and thought this would be the perfect place to express them. Here they are; thank you for your responses in advance.

~ I can easily install the 8.42 LTS installation from the Ubuntu website, but I did however notice that there are several different types to download from other sites. (Amd, x386, or etc. - My terminology may be incorrect.) My question is, what is the default 8.4 LTS installation. I have an AMD 64x2 chipset.

I am installing Hardy due to the fact that Intrepid gives me the known IRQ errors upon installing.

~ I have an Nvidia 8800GTS 512MB Overclocked. Ubuntu pulls up the name of my video card, but does not display my RAM or etc. on the card itself. It only shows question marks w/ SystemInfo. How do I properly upgrade my card to know I am getting the most performance out of it?

Thank you all in advance.

-Jason R. Bush
Ann Arbor, MI

---

### Post by plucky on 2009-03-11
~>  I can easily install the 8.42 LTS installation from the Ubuntu website, but I did however notice that there are several different types to download from other sites. (Amd, x386, or etc. - My terminology may be incorrect.) My question is, what is the default 8.4 LTS installation. I have an AMD 64x2 chipset.


Open a terminal **Applications > Accessories > Terminal** and input ```
uname -a
``` will tell you what version you have installed.

If it is i686 = 32 Bit
If it is x86_64= 64 bit

> ~ I have an Nvidia 8800GTS 512MB Overclocked. Ubuntu pulls up the name of my video card, but does not display my RAM or etc. on the card itself. It only shows question marks w/ SystemInfo. How do I properly upgrade my card to know I am getting the most performance out of it?

Not sure about this,but you might have to install the driver for this card.Go to **System > Administration > Hardware Drivers** and see what drivers the system wants to install.Or search the forum for 8800GTS and see what others recommend.

From a terminal ```
sudo lshw
``` will display information about your hardware.


Good Luck

---

### Post by skymera on 2009-03-11
If you have the Nvidia driver installed correctly.
All your 8800GTS information would be available from the Nvidia Settings panel.

---

