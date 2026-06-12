---
title: "Blurry font prob"
date: 2005-01-26
forum: Desktop Environments
---

### Post by Sham on 2005-01-26
Hi Guys,

The fonts on my system look really faint and blurry. I posted on the XFree  forum, but seeing as this doesn't appear to be the prob I was hoping to have more luck here. If I may direct you towards:

[http://ubuntuforums.org/showthread.php?t=12674](http://ubuntuforums.org/showthread.php?t=12674)

?

Any input would be appreciated.

btw, its a warty install running Gnome.

---

### Post by albersag on 2005-01-26
[QUOTE=Sham]Hi Guys,

The fonts on my system look really faint and blurry. I posted on the XFree  forum, but seeing as this doesn't appear to be the prob I was hoping to have more luck here. If I may direct you towards:

[http://ubuntuforums.org/showthread.php?t=12674](http://ubuntuforums.org/showthread.php?t=12674)

?

Any input would be appreciated.

btw, its a warty install running Gnome.[/QUOTE]
 Autohinting did not resolve anything?.

I

---

### Post by Sham on 2005-01-26
[QUOTE=albersag]Autohinting did not resolve anything?.

I[/QUOTE]

I'm not sure if what I have at the moment is autohinting already. If i go to Computer -> Desktop Prefs >Fonts, in the first instance I have Subpixel smoothing enabled, and when I click on details the hinting is on full. The sub pixel order is on BGR.

Is this the same thing? Im getting a little confused  :-k

---

### Post by albersag on 2005-01-26
On shell type


sudo dpkg-reconfigure fontconfig

In the menu it appears selec autohinting off. I think remember is the last option. Then Enter, enter, until it exits..

Then restart X window (Contrl+Subsr)

---

### Post by Sham on 2005-01-26
[QUOTE=albersag]On shell type


sudo dpkg-reconfigure fontconfig

In the menu it appears selec autohinting off. I think remember is the last option. Then Enter, enter, until it exits..

Then restart X window (Contrl+Subsr)[/QUOTE]

Just to clarify, does it need to be on or off?

---

### Post by bazuka on 2005-01-26
albersag just suggested what I was going to. Sub-pixel rendering uses just one or two of the three color channels instead of all three; in some cases giving you text that's easier to read. The BGR thing is the order of the pixel color from left to right, Blue first, then Green, and then Red. On the left side of each character, hinting it would enable the red channel of the pixel in attempt to make it smoother.


Someone please correct me if I am mistaken on that.

---

### Post by Sham on 2005-01-26
[QUOTE=bazuka]albersag just suggested what I was going to. Sub-pixel rendering uses just one or two of the three color channels instead of all three; in some cases giving you text that's easier to read. The BGR thing is the order of the pixel color from left to right, Blue first, then Green, and then Red. On the left side of each character, hinting it would enable the red channel of the pixel in attempt to make it smoother.


Someone please correct me if I am mistaken on that.[/QUOTE]

In the details section of the fonts screen, the pixel order is BGR. What you are saying is that I should disable this feature, or enable?

Sorry if I sound dumb. Its been a loooong day......

---

### Post by bazuka on 2005-01-26
You want to select the option to turn autohinting off if it is there. If not, do "sudo dpkg-reconfigure fontconfig" from the command line and turn it off when prompted. Off topic, but I assume you're using an LCD monitor on that box, correct?

---

### Post by Sham on 2005-01-26
[QUOTE=bazuka]You want to select the option to turn autohinting off if it is there. If not, do "sudo dpkg-reconfigure fontconfig" from the command line and turn it off when prompted. Off topic, but I assume you're using an LCD monitor on that box, correct?[/QUOTE]


Thats right, I am using an LCD screen. Thanks for the help. I'll let you know how it goes.

---

### Post by albersag on 2005-01-26
In order to clarify you have to select the option 1 or 3.

Screenshot in spanish attached

Other things i have done is increese dpm to 100 and monocrome render. Thats how i see the fonts better. Not as in other Os, but when i have time, i will investigate it more  :-({|=

---

### Post by Sham on 2005-01-26
[QUOTE=albersag]In order to clarify you have to select the option 1 or 3.

Screenshot in spanish attached[/QUOTE]

I just tried it on a testbox. It didn't look like yours, but I get the idea. Cheers.

---

