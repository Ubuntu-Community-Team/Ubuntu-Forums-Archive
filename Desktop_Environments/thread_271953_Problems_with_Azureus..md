---
title: "Problems with Azureus."
date: 2006-10-05
forum: Desktop Environments
---

### Post by Brenlae on 2006-10-05
You see, I manually installed Azureus to the /opt/ directory. I have a desktop script (if you can call it that) with the following in it:

[Desktop Entry]
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

Now, it appears fine under Applications>Internet, but when I click on it to execute it, an error pops up saying:

Could not launch menu item

Details: Failed to execute child process "/opt/azureus" (Permission denied)

But when I double click on azureus when surfing around its directory, it executes just fine.

Could somebody help? I really like azureus and would like to get this resolved. :(

---

### Post by skymt on 2006-10-05
I'm betting the actual Azureus program is at "/opt/azureus/azureus".

---

