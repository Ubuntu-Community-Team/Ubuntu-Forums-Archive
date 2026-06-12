---
title: "Keyboard-layout switching button does not stick"
date: 2008-08-06
forum: Desktop Environments
---

### Post by zyanide on 2008-08-06
Hi,

I am using (trying to actually) two kb layouts (US/Thai) but, I got few problems.

My default layout is US. When I add Thai as my second layout (along with a button to switch between the layouts) in the Keyboard Preferences, it works ok.

However, every time after I reboot, the key layout changes back to US ONLY.
One of my friends suggested that there is a problem with the permission of xorg.conf.

So I edited the file myself using: sudo vim /etc/X11/xorg.conf

What I did is I add "th" behind the XkbLayout option:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us,th"
EndSection

Doing so, I have the two layouts working simultaneously but I still have to set the layout-switching button every time I log in.
Anyone has any idea how to fix this?

Thanks a lot!

---

### Post by adam.smith on 2008-08-06
no solution - just seconding the issue. In the keyboard indicator this looks very odd: It formally still shows me all three keyboard layouts (Spanish, German, US in my case) installed, but I can only use the US one. If I revert to default and then install the two others they work fine until reboot, when the issue reoccurs as described above.
Also, the little indicator for keyboard indicator still switches between two (instead of three) languages, but without any effect on the actual layout.
The layout switching button is also reset with each reboot.

I had this working smoothly under 7.10, problem started with update to 8.04.

Any help appreciated.

---

### Post by zyanide on 2008-08-07
So, it is not just me then. :P

---

