---
title: "Password/keyring question"
date: 2009-05-29
forum: General Help
---

### Post by Carl H on 2009-05-29
I've recently installed Ubuntu 9.04 on my Dell 1300, and it works like a charm, even the Broadcom 4318 wireless with WPA-PSK encryption. :D

The only problem I've got, and this is obviously of my own doing, is that on boot it prompts me for the password for the keyring so that the Network Manager applet can access the password for the wireless. I then have to manually select and connect to my wireless network.

I've also put 9.04 on my Asus EeePC 701 (also works like a charm), and that doesn't ask for any such password, it just auto-connects the wireless on bootup. 

What do I need to do to stop being prompted for the password?

---

### Post by Soul-Sing on 2009-05-29
1. right click Network Manager icon in system tray
2. Edit Connections -> Wireless -> select your wireless connection -> Edit
3. tick 'System setting' and 'Connect automatically' if not done already

System - Administration - Login window:  "security": automatic login.

I hope this will be helpful.

---

### Post by Carl H on 2009-05-29
Thank you.

There does not appear to be "system setting" in Network Manager, but "Connect Automatically" is ticked. 

I have already got the Login Manager set to Automatic. 

Maybe I didn't explain the problem very well. I want to allow Network Manager to have access to the keyring automatically, without asking for the password. 

Thanks in advance.

---

### Post by Soul-Sing on 2009-05-29
: [http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)

I think this a better way to solve your issue.

---

### Post by pastalavista on 2009-05-29
The easiest way to avoid the keyring is to click 'cancel' the first time it asks for a keyring password. To fix it, open network manager and delete all the wireless connections it has saved. Then, next time you connect and it asks for a keyring password, just click cancel. I'm not sure I even understand the reason for a keyring, but I'm sure it makes the security paranoids feel better.

---

### Post by Carl H on 2009-05-29
Thanks for the replies.

Ticking the "available to all users" box did the trick.

---

