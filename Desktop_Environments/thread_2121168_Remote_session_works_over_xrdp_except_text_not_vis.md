---
title: "Remote session works over xrdp except text not visible in terminal emulator"
date: 2013-03-01
forum: Desktop Environments
---

### Post by PeterTaps on 2013-03-01
Folks,

I have installed a minimal version of Ubuntu server 12.10 + openbox. I also installed xrdp.

I am able to create a new remote desktop session from a Windows machine. The browser and other apps seem to work. My only problem is with the terminal emulator. Althouth the emulator window gets created, the prompt is not visible. If I type in, for example, ls, in the window, I now see a list of files. However, what I typed itself is not visible.

Essentially, I don't see the prompt and anything that I type in the emulator window.

I am wondering if anyone can tell me what could be the problem here. This is a fresh install with no additional software except xrdp and firefox.

Thank you in advance for your help.

Regards,
Peter

---

### Post by PeterTaps on 2013-03-01
I found the problem. It appears the text is written in black. If I create a new xterm as "xterm -bg white," I can see my text.

To fix it, I modified ~./Xresources and changed XTerm*background: white. However, it didn't make any difference even after the reboot.

Does anyone know how to fix the background for xterm?

Thank you in advance for  your help.

Regards,
Peter

---

