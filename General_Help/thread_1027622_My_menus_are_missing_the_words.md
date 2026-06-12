---
title: "My menus are missing the words?"
date: 2009-01-01
forum: General Help
---

### Post by er0k on 2009-01-01
Strange problem... I just did a clean install of 8.10 and in apps like Open Office and Picasa, the menus are missing all the words. The menus are still there and usuable, but you can't read any of them :confused:

Maybe a font or a language problem? Here's some screenshots

[img]http://er0k.org/up/put/mom-menu_openoffice.png[/img]

[img]http://er0k.org/up/put/mom-menu_picasa.jpg[/img]

Any suggestions?

---

### Post by alzie on 2009-01-01
I did some searching and found some similar problems.  There is a bug that affects older nVidia cards using the 96 series drivers here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076)

Here is a solution offered from the same link:


>  TexasRanger wrote on 2008-11-18: (permalink)

My symptom:
With Ubuntu Visual Effects set to "Normal" or "Extra", OpenOffice menu text disappeared.

After several days of experimentation, I can report the following:
- I am running Ubuntu 8.04 LTS with Ubuntu release of OpenOffice 2.4.1 and Nvidia driver 96.43.09-0ubuntu1 graphics card driver.

- When I enabled Compiz Normal or Extra Visual Effects, the menu text in all OpenOffice apps disappeared, replaced thin horizontal lines. Problem does NOT occur with Visual Effects set to "None". No other apps displayed the symptom, only Oo.

- After experimenting, I found that Oo fonts could be restored by disabling "antialiasing" checkbox in the Oo Tools/Options/View submenu. Of course, this made the menu text fonts look very pixel-y.

- Problem solved (for me) by running "sudo dpkg-reconfigure fontconfig-config" and selecting "Autohinter", "Always" (for subpixel rendering on my LCD display), and "No" for Enable bitmapped fonts. Then, I changed Ubuntu System/Preferences/Appearance/Fonts to "Subpixel" smoothing. Viola! Problem solved.


Another option is to set Visual Effects to none in your Appearance Preferences.

I hope this helps

---

### Post by er0k on 2009-01-01
ah, I should have figured. I had trouble with this video card in Hardy, too. I didn't really know what to search for though...

I set the visual settings to none, works for me. Thanks! :)

---

### Post by rtowsley on 2009-04-09
Thanks that worked for me too. No visual effects. Thanks again

---

