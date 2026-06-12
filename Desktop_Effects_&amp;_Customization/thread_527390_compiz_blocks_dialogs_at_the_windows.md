---
title: "compiz blocks dialogs at the windows"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by zeph7r on 2007-08-16
I have a acer aspire laptop with a mobility radeon x600 and i'm experiencing  poor performance with compiz 0.3.7 in ubuntu feisty fawn. In the  sessions option dialog I activated the option to automatically save changes to the session, so when I log out and in again, I experience that the windows loose they're dialogs, for example, firefox doesn't show it's menus and the content of web pages. If I disable desktop effect everything goes to normal, but I didn't wan't to have to do that... If i enable them back, now almost everything is normal, except some menus from the gnome bar that don't show the selection signal when the mouse is passing by the application shortcuts, and the exit screen, that doesn't show up no matter how many times I click on it, only to appear several minutes later, totally unexpected. Any workaround to this? Also, where do I get/what repos should I add in order to get a more updated version? Stable is already 0.4.0 ... And compiz fusion is already out there and I couldn't find it in the unsupported repo.

Cheers

---

### Post by zeph7r on 2007-08-17
I've just updated to last versions available at treviño's repositories (which are 0.5.1) and besides the new plugins I just installed, everything is behaving the same way, except opening the logout screen, which now functions. Isn't this supposed to be strange? Perhaps the opensource drivers (which I'm currently using) don't support desktop effects completely.. May this be the case? Should I install the ATi ones instead?

---

### Post by zeph7r on 2007-08-18
since I installed ATi's binary drivers before, may it be because of that?

from [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> Removing the proprietary fglrx driver

fglrx is the name of the closed-source, proprietary driver from ATI. It conflicts with the open-source "radeon" driver. If the "fglrx" kernel module is loaded at boot, X will be able to start using the "radeon" driver but "Direct Rendering" (DRI) will be disabled. This results in a severe performance reduction. If you previously used the proprietary "fglrx" driver it is highly recommended to unload the "fglrx" module if you wish to use the open-source "radeon" driver. This can be done with:

sudo modprobe -r fglrx

To prevent the loading of this module at boot, you may blacklist it.



---

