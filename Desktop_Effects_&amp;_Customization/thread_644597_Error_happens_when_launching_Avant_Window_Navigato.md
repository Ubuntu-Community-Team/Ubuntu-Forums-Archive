---
title: "Error happens when launching Avant Window Navigator"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by Jeffrey.Lee.Li on 2007-12-19
I've installed Avant Window Navigator successfully using "sudo apt-get install" from source list in Ubuntu 7.10 (Gutsy Gibbon) but it didn't work as expected.

I can open Awn manager normally via System/Preferences/Awn manager. Yet when I select Applications/Accessories/Avant Window Navigator, there's only a splash at the bottom of screen and nothing more:confused:.

I tried avant-window-navigator in Terminal and got Error Codes below:
-------------------------------------------------------------------------------------------
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
-------------------------------------------------------------------------------------------

Hm~It seems to refuse to show up without enabling Desktop Effects with Compiz & Emerald, which is exactly the very thing I can't do with my computer powered by VIA/S3G Unichrome Graphic Card (Model: P4M800Pro).

***So, could it be possible to make AWN run without enabling Desktop Effects?***
or
***Can someone show me a way to install an appropriate driver in order to  enable Desktop Effects under my current hardware configuration?***

BTW: I tried VIA's official VIA/S3G Unichrome Graphic Driver for Linux XFree86 which declared success in enabling Desktop Effects but failed:(. After installation successfully, as I can't see any error during installation process, I have to log in X Window and work under 800x600 resolution 'cos none above that is supported.

Thanks guys & any helping clue is appreciated here:)

---

### Post by Nano Geek on 2007-12-19
I think that Desktop Effects only work with ATI, Nvidia, or Intel graphics cards, and no, AWN will not run without compositing.

However, you could try xcompmgr. It's basically a light-weight Desktop Effects.```
sudo apt-get install xcompmgr
```

Just run it from the command-line then try AWN again.

---

### Post by Jeffrey.Lee.Li on 2007-12-19
Thank you very very very much asjdfwejqrfjcvm msz34rq33. It works for me. So great. Yeah~~~:)

BTW I wish everyone in UbuntuForums A Merry Xmas & Happy New Year~~~:)

---

### Post by Nano Geek on 2007-12-19
Glad it worked, and a Merry Christmas to you too.

---

