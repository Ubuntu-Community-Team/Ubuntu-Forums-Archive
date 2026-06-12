---
title: "[SOLVED] Xfce Issue: Desktop Settings"
date: 2007-04-27
forum: Desktop Environments
---

### Post by drakos on 2007-04-27
So I've been having a strange problem where it seems that every time I reboot, Xfce is no longer set to manager the desktop, so my backgrounds disappear. Then after I open up the Desktop Settings window and check "Allow Xfce to manage the desktop" and close it again, it will uncheck itself.

I've gone into $/.config/xfce4/mcs_settings/desktop.xml  and changed the value that should be controlling this, but it resets every time I log out.


Here's the line I change:
<option name="showdm" type="int" value="0"/>

Should be a "1" I assume, and it seems to work until I reboot.

---

### Post by john.nicholls on 2007-04-27
Do you have "Automatically save session on logout" checked in Sessions and Startup?

---

