---
title: "Keyboard Shortcuts - Character Codes"
date: 2006-07-16
forum: Desktop Environments
---

### Post by srinig on 2006-07-16
In Ubuntu-Gnome, when I open System->Preferences->Keyboard Shortcuts, I see that shortcuts to some operations are disabled, some are assigned shortcuts and there are some other operations having strange character codes to their right, like '0xb2' to launch a web browser, for example. What does this 0xb2 mean? does this correspond to some key in the keyboard? I know I can assign my own keys to open a web browser, but I would prefer using the default shortcut (if at all '0xb2' correspond to some key or key combination). Thanks in advance for any help or clarification with this.

---

### Post by asimon on 2006-07-16
0xb2 corrosponds to the key symbol XF86HomePage. A lot of keyboards nowadays have speacial media keys, to start a mail application, browsers, mute sound, increase or decrease volume, etc. If kernel and X both support the keyboard and everything is configured right pressing for example the Browser key should result in a 'XF86HomePage' key event (the file /etc/X11/xkb/symbols/inet lists most of them).

In the end it's a usability issue, i.e. a bad user interface. There should not appear '0xb2' but something like "Web Browser Key" or at least "XF86HomePage". I hope this gets fixed some day.

---

### Post by srinig on 2006-07-16
OK, I got it. Thanks for that piece of info. Yes, as you said, it should be displayed as 'Browser media key' or something like that. 

I don't like using those media keys anyway... I have just assinged Ctrl+Alt+b to open my browser. Thanks again for your information.

---

