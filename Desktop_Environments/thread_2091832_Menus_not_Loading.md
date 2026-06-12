---
title: "Menus not Loading"
date: 2012-12-06
forum: Desktop Environments
---

### Post by FelixRulz on 2012-12-06
I installed Ubuntu 12.10 a few days ago. It's running along side my Windows 7 install (i.e. duel boot).

I had a problem today... when I start Ubuntu none of the menus load (both the one along the top and the one on the left). I can open the terminal using ctrl+alt+t and also the ctr+alt+f? terminals.
The desktop icons are visible and I can right click. I created a file using right click, giving it a .htlm extension allowed me to open firefox.
The close, minimise and maximise buttons are not visible and instead of the hidden scroll bars they are now always visible. If I double click firefox's menu bar (I thought this should maximise) the program crashes instead. It also doesn't allow me to click and drag to resize.

This is my first serious attempt at using Ubuntu/Linux so I'm not very familiar with diagnosing/fixing what is wrong. Any help would be great. Thanks.

---

### Post by COMECON on 2012-12-06
Try running this on a Terminal:
```
 $ sudo apt-get install linux-headers-generic nvidia-current nvidia-settings 
```
If you have a NVIDIA graphics card, of course. If you have an AMD/ATI card, do this:
```
 $ sudo apt-get install linux-headers-generic fglrx-updates 
```

Then restart the computer and you should be running with your graphics card drivers, perhaps this will solve the bug.

Catbuntu

---

### Post by FelixRulz on 2012-12-06
> **COMECON said:**
> If you have an AMD/ATI card, do this:
```
 $ sudo apt-get install linux-headers-generic fglrx-updates 
```
Catbuntu

Thanks for the reply, but unfortunately the symptoms persist.

I'm not sure if this will help but I have been playing with the graphics drivers recently.
I had some problems with Wine lagging so was trying to update my ATI drivers. I installed 'Additional Drivers', then went to "System Settings">"Software Sources">"Additional Drivers" and changes to one that wasn't recommended. [See bottom of [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)]

---

### Post by FelixRulz on 2012-12-07
This message appears after leaving the computer for some (variable) time:

"The application Compiz has closed  unexpectedly."

---

### Post by FelixRulz on 2012-12-07
I have fixed the problem. Comecon was correct in that it was to do with the video drivers.

To revert back to the original drivers I right clicked the desktop, then used "change desktop background" to access the other system settings. Then went to "Software Sources">"Additional Drivers" and changed back to the one marked as "(open source, tested)" (See attached pic).

Now I can continue learning to use Ubuntu.

---

