---
title: "Radeon 7000 Wont install 8.04 Hardy Problems..."
date: 2008-12-23
forum: General Help
---

### Post by EDH1981 on 2008-12-23
I am Having problems getting my Ati Radeon7000 too work on hardy 8.04 Want 3d desktop effects too work as well can someone help me with this issue here is what i have for you....


00:03.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


Xorg File ....

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"

Thank You very much!

---

### Post by davidgeeee on 2008-12-23
I am interested too since my 'lspci' give me:
> ATI Technologies Inc Radeon RV100 QY
as my graphics card.  Reconfiguring xserver gives me a generic xorg.conf

---

### Post by Aijse on 2008-12-27
Hi,

I myself am pretty new to all this aswell but I might be able to point you to a thread I just read that might have some usefull info.

[http://ubuntuforums.org/showthread.php?t=1022552&highlight=Radeon+7000+](http://ubuntuforums.org/showthread.php?t=1022552&highlight=Radeon+7000+)

in your xorg it says you use the vesa driver, you should get ati or fglrx there, as is explained in the thread I previously mentioned.


Hope this helps (Just ebayed me such a graphic card so I'm interested whether you got it working or not.)

--Aijse--

---

