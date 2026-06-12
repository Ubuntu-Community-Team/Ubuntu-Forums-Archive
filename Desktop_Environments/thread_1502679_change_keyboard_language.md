---
title: "change keyboard language"
date: 2010-06-05
forum: Desktop Environments
---

### Post by orengolan on 2010-06-05
I installed japanese in 'Language Support' (so I'll have both English and Japanese) and I logout.
In the login screen I see other languages - Chinese and Taiwanese but not Japanese. 

Also, I notice a selectbox - 'keyboard input method system'
but not sure if I need to change it.

Thanks!

---

### Post by Ron S on 2010-06-05
Try going to preferences-keyboard in your main menu. Click on the Layouts tab and then click on add to bring up a list of keyboards and languages and select Japanese. Hope this helps

---

### Post by orengolan on 2010-06-05
there is no layout tab -
[https://bugs.edge.launchpad.net/ubuntu/+source/lxinput/+bug/529597](https://bugs.edge.launchpad.net/ubuntu/+source/lxinput/+bug/529597)


are you sure it's related to layout? i want to TYPE in Japanese, not change my desktop to Japanese.


thanks!

---

### Post by orengolan on 2010-06-12
I followed this steps and installed scim
[http://ubuntuforums.org/showthread.php?t=27811](http://ubuntuforums.org/showthread.php?t=27811)

in scim setup form I don't see japanese under 'global setup'.
I see the following checkboxes:
English/European, RAW CODE and UIM-direct.

under 'language support' I have japanese checked.
I also tried changing the 'keyboard input method system' selectbox to scim and scim-bridge but i still don't see japanese in scim setup.

any tips?

---

### Post by Jorge Alban on 2010-06-12
I tried several keyboard-layout switching hacks for Lubuntu 10.04 and what finally did it for me was to add the following two lines

```
Option "XkbLayout" "us,es"
Option "XKbOptions" "grp:alt_shift_toggle"
```

to /usr/lib/X11/xorg.conf.d/05-evdev.conf

at the "InputClass" section, right under the Driver "evdev" line.

I used "us,es" in order to switch between spanish and english with a hit of the alt+shift keys. 

More info here:

[http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html]("http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html")

---

### Post by orengolan on 2010-06-13
thank you Jorge, but it didn't work for me.
(i used jp).

I also have scim running (and i see a the scim keyboard icon on my panel). i disabled scim but it still didn't let me write in japanese.
 
do i need to uninstall scim?
how do i make sure I have the correct Japanese that works with your method. i checked the Japanese checkbox under 'Language Support'. is that enough?

Also, are there any visual indicators when u switch language?
(I didn't notice anything).

---

### Post by simosx on 2010-06-13
What I see here is that three things are being mixed together, producing strange results.

1. For Latin, Cyrillic, Greek and the vast majority of the (non-complex) scripts, you need to use the 'XKB' support that comes with the X server. This is the settings at System/Preferences/Keyboard/Preferences. To make sure that this basic input method support is used, look into System/Administration/Language Support and make sure that nothing is selected in the 'Input Method' drop-down menu. If you just changed this, you need to re-login to take effect.
There is a Japanese keyboard layout in the Keyboard settings, though it is for something called 'Kana'.

2. If you need more advanced input methods, which includes Japanese, you need to enable a different input method. If you have Ubuntu 9.10, then this advanced input method is called SCIM. However, in Ubuntu 10.04, SCIM is replaced with IBus. So, if you have Ubuntu 10.04, try to make this work with IBus, otherwise you are messing with your system in unknown ways. 

3. The proper advanced input method in Ubuntu 10.04 is IBus. You enable from System/Administration/Language Support (see the Input Method dropdown menu), then re-login or restart. You configure from System/Preferences/IBus Preferences.

I do not speak Japanese or any similar languages with complex writing. If you do and you can make the settings work with IBus, with the minimum configuration/hassle, I would love to see your blog post (or UbuntuForums thread). :-)

EDIT: Actually, here is a good post on using IBus properly for Japanese, [http://swiss.ubuntuforums.org/showthread.php?t=1473389](http://swiss.ubuntuforums.org/showthread.php?t=1473389)

---

### Post by orengolan on 2010-06-13
thanks! i'll check out the thread about IBus.

---

