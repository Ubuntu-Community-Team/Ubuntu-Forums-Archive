---
title: "beryl problems"
date: 2008-04-12
forum: Desktop Environments
---

### Post by methodtwo on 2008-04-12
Weeel i installed beryl today and i upgraded my nvidia driver(there is now an nice nvidia sign that comes up just before gdm......Unlike in gentoo when i made the mistake of ticking nvidia framebuffer in the kernel compilation so that i had to use the nv driver instead of  the nvidia driver...yawn yawn yawn i here you go!).Well the nvidia driver is installed correctly.I can run beryl-manager and have it set up to come up on boot....but well there doesn't seem to be any change....i.e i've tried preesing the arrow keys to revolve to desktops and see that cube but nothing happened.Also there is no bendy windows 'n ting.
Here is my /etc/X11/xorg.conf..well just the relevant parts:
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
I'm still guessing the this problem is at the beryl level not at the X and drivers level coz when i do $glxinfo | grep direct .......i get: direct rendering: yes.I found a forum discussion, but this was refering to ubuntu on a mac book and the advice was to make sure 915resolution was installed.Have you any ideas as to what the problem could be...and what might be missing in my installation? Oh and something else: the 1st time i started beryl-manager i got a missing module error or something..but subsequent runs of beryl-manager have been successful(i think)...well i mean i just get this like pop-up menu.Also i tried switching the window manager to beryl instead of metacity and disaster occurred.The screen went all funny colored and totally shitty.
Any ideas would be great my gurus.Thankx in advance

---

