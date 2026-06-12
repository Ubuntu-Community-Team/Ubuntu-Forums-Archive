---
title: "Enabling root logins in gdm"
date: 2007-12-25
forum: Desktop Environments
---

### Post by akwatve on 2007-12-25
AFAIK each login manager i.e. kdm and gdm has a configuration file which is used to decide whether to allow root to login or not. By default this file has something like "AllowRoot=false" which disables root logins in Ubuntu/Kubuntu.

I changed this to "AllowRoot=true" in kdm config file and it worked. However, in gdm config files "/etc/gdm/gdm.conf" and "/etc/gdm/gdm.conf-custom" Just manually changing true to false is not working. However, when I tried to do this using the GUI (i.e. the LoginWIndow application), it worked. The file modification timestamps show that only one file "/etc/gdm/gdm.conf-custom" was changed when I ran the "LoginWindow". I noticed that instead of changing true to false the GUI simply removes that line when root logins are enabled. I tried to do that as well but no success.

I don't understand what else is required to enable root login. Is there somthing else that GUI is doing but I am not. Note that I do not need root logins, I just want to understand how things work ...

---

### Post by TidusBlade on 2007-12-25
I am pretty sure you can enable root logins in the user/account management section of the Settings?

---

### Post by akwatve on 2007-12-25
Let me make myself clear here. I know that there are GUIs to enable root logins. All I want to know is what configuration files do they modify. I was under the impression that gdm (like kdm) has only one config file (gdm.conf or gdm.conf-custom). But I think there is something more needed to be done, in addition to changing this one file.

---

