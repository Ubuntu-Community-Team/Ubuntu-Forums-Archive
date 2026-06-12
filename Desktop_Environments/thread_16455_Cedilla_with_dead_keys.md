---
title: "Cedilla with dead keys"
date: 2005-02-21
forum: Desktop Environments
---

### Post by easy_target on 2005-02-21
I finally installed my keyboard with dead keys so I could utilize accent marks properly. My primary language is portuguese, which uses accent marks AND cedilla. However I haven't been able to make cedilla work with several applications like openoffice and most editors. The only way around is use the character map, copy and paste the cedilla every time, which is very time consuming. Is there a way of enabling cedilla using apostrophe + letter c (or something like that)?

Thanks

---

### Post by dtessier on 2005-02-22
<right-win> , c works for me (that's the right window key, or whatever your key is set to activate dead-keys, then a comma, and then c).

---

### Post by easy_target on 2005-02-24
Do you have to configure it? Every time I try it comes out as a "c" with and accent mark. Funny it works with Open Office but not with Evolution

---

### Post by dtessier on 2005-02-26
Strange, it works fine for me even in Evolution. The way I configured it was to go to System->Preferences->Keyboard (at least that's the menu for Hoary), then select the Layout Options tab, and then click on the arrow next to compose to bring down the options, and finally I choose which key activates the compose option (the right windows-key in my case).

---

### Post by easy_target on 2005-02-27
Thank you very much dtessier. I followed your steps (I still have warty because I use this computer as a printer server on the network and if I break it my wife kills me) and they were very easy to follow. Now I  can get the cedilla everywhere. Thank you for the tip, it helped me a lot! 

Cheers  =D>

---

### Post by easy_target on 2005-05-31
Okay. I know it sounds stupid but I tried to install the lates ATI drivers in order to get better performance. Everything went fine except for the fact that I get an annoying message everytime I boot up the computer or when I try to change keyboard configurations from Gnome that goes: 
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b> 
What is going on? Any help is appreciated.
By the way my keyboard is a Microsoft Internet Keyboard Using US international with dead keys.

---

### Post by ispmarin on 2006-02-08
Is there any solution that does NOT use the altgr or winkey to get cedila? Use in the old fashion: apostrofe plus c?

Thanks.

---

### Post by codas on 2006-09-14
Dear All!

Is there a way to type cedilla with ' + c ?

I wouldn't like to type Alt, Ctrl, or any other special key...

Thanks!

Best regards,
Daniel

---

