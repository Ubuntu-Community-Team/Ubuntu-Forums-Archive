---
title: "Problem with Keyboard Layout"
date: 2006-08-20
forum: Desktop Environments
---

### Post by coleing on 2006-08-20
Hi,

I am a UK user, and I cant seem to get my keyboard layout correct.

I have a logitech elite keyboard, and my @ and " are mixed up.

I also would like to know how to get ubuntu to remember my numlock and f-lock settings. (ie. I need thm both enabled at startup).

Any help appreciated. I have played with the keyboard layout settings, but it doesnt seem to change anything.

---

### Post by meng on 2006-08-20
Which layouts have you tried that didn't work as desired?
Install numlockx for numlock enabled by default. I'm not sure about Flock though.

---

### Post by coleing on 2006-08-21
Ive tried a number of logitech layouts, and also most of the generic keyboards.
None of them put the " on shift+2 and none of them put he @ on its normal key  to the left of the tilda.

---

### Post by meng on 2006-08-21
No, I don't mean keyboard model, I mean layout, as in US or UK.
I think you may have it set to a UK layout when you want a US layout. Just because you're a UK user doesn't mean you need a UK keyboard layout.
System > Prefs > Keyboard > Layout > Add > US English

---

### Post by Malac on 2006-08-21
In System->Preferences->Keyboard then Layout Tab.
Try "Generic 105-key (Intl) PC" in model and "United Kingdom" in layout.
This works for me with @ " etc.

---

### Post by coleing on 2006-08-21
I have tried both of the settings above, but it doesnt make a difference.

For info, I installed ubuntu 6.06 LTS, and then upgraded from Gnome to KDE.

Im pretty sure the keyboard has not been correct throughout though.

I dont have the same menu options, but I tried changing to UK Intl 105 keyboard and US, and UK, but neither worked for me.

---

### Post by coleing on 2006-08-21
Ok - some more info.

I enabled the little system tray icon, which says "err" on it.
When I hover over it, it says

Error changing keyboard layout to 'us'

---

### Post by meng on 2006-08-21
Ahhh! That's interesting, although I'm not sure why that error occurred.
One option would be
ctrl-alt-f1
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
and choose us keyboard layout.

Then
sudo /etc/init.d/gdm start

Not sure if the gdm stop/start is necessary, but hopefully it should bypass whatever error you are currently getting.
Let me know when it doesn't work - I don't have a good feeling about this!

---

### Post by coleing on 2006-08-22
THanks, I managed to totally screw my system, as I chose a whole heap of wrong options in xserver-xorg confiuration.

However, I am now quite please with myself for being able to fix it.

BUT - My keyboard problem still persists. It still has the "err" saying it cant change the keyboard to 'us'.

Any more help?

---

