---
title: "compiz not working..."
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by Mia_tech on 2008-02-19
I've just installed gutsy and compiz is not working this is what I have for video card

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

does anyone know if compiz works under ATI or is there a way around it to make it work?

thanks

---

### Post by luisromangz on 2008-02-19
It works with ATI cards, if you are using the newer fglrx drivers with AIGLX, if not with XGL. But I don't know about your specific card, which seems to be quite old.

---

### Post by northern lights on 2008-02-19
The recent ATIs need fglrx with XGL or what not - that old a card works fine with old drivers also, on top of that, I don't even think it's supported by XGL. I think it needs "ati" drivers there might be one especially for rage 128, not sure. You can check [here]("http://www.calel.org/pci-devices/xorg-device-list.html#ATI").

Further, what exactly do you mean by compiz "not working"? Any error message?

[EDIT]checked the list myself, apparently driver's called "r128"[/EDIT]

---

### Post by Mia_tech on 2008-02-20
> **northern lights said:**
> The recent ATIs need fglrx with XGL or what not - that old a card works fine with old drivers also, on top of that, I don't even think it's supported by XGL. I think it needs "ati" drivers there might be one especially for rage 128, not sure. You can check [here]("http://www.calel.org/pci-devices/xorg-device-list.html#ATI").

Further, what exactly do you mean by compiz "not working"? Any error message?

[EDIT]checked the list myself, apparently driver's called "r128"[/EDIT]

This is the error I got

jorge@kubuntu-box:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting


thanks

---

### Post by neverliveneverdie on 2008-03-02
> **Mia_tech said:**
> This is the error I got

jorge@kubuntu-box:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting


thanks
ok well first of all i am pretty much a noob to linux, i run ubuntu but taking the assumption that it can't be much different then kubuntu im going to try to help. i had the same problem.

what i had to do was go into the restricted driver manager and activat ATI which downloaded and activated the ATI drivers. after that was done and i restarted my computer i downloaded the package xserver-xgl. and then my compiz worked. after that i installed a compiz manager so that i could customize my effects. i hope this works for you. GOOD LUCK!

---

### Post by northern lights on 2008-03-02
Run ```
sudo apt-get install xserver-xgl
``` and then change to xclient session during login.

---

### Post by Mia_tech on 2008-03-03
> **neverliveneverdie said:**
> ok well first of all i am pretty much a noob to linux, i run ubuntu but taking the assumption that it can't be much different then kubuntu im going to try to help. i had the same problem.

what i had to do was go into the restricted driver manager and activat ATI which downloaded and activated the ATI drivers. after that was done and i restarted my computer i downloaded the package xserver-xgl. and then my compiz worked. after that i installed a compiz manager so that i could customize my effects. i hope this works for you. GOOD LUCK!

well...in my install the ATI driver is not showing in the restricted driver manager..

---

### Post by neverliveneverdie on 2008-03-03
> **Mia_tech said:**
> well...in my install the ATI driver is not showing in the restricted driver manager..

ok well, there is another way around that. I've heard of a program called Envy. I would suggest trying that. I beleive its made for Ubuntu but ive heard of people trying it on kubuntu, i haven't found any response to whether it worked or not though. i would look into that? and personaly i think you would be better off with ubuntu, there is much more help forums for ubuntu than kubuntu. but i hope this works ^.^

---

