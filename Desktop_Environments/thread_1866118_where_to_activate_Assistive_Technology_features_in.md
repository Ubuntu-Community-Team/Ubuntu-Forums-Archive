---
title: "where to activate Assistive Technology features in Ubuntu 11.10?"
date: 2011-10-21
forum: Desktop Environments
---

### Post by chenjianyyzz on 2011-10-21
**Hello, **
 
**I am try to use LDTP, and it's said that the [COLOR=#ff0000]Assistive[/COLOR]** Technology features need to be activated, but I can not find where to activate, my Ubuntu is 11.10, does any one be kind to help?
 
my mailbox is: [EMAIL="jian.chen@leica-microsystems.com"]jian.chen@leica-microsystems.com[/EMAIL]
 
Thanks in advanced

---

### Post by mcduck on 2011-10-21
Click the Shutdown/Settings icon in the top right screen corner (just right from your user name). Select "System Settings", and you'll find the "Universal Access" options there.

---

### Post by chenjianyyzz on 2011-10-21
Thank you, mcduck, 
 
but from the "Universal Access", I can not find the checkbox like "Enable assistive technologies", it seems in this version of Ubuntu, the assistive technologies is devided into several parts, like "Seeing", "Hearing, "Typing", "Pointing and Clicking"
 
and now what I want to do is to use the LDTP, I don't know which option should I turn on,
 
do you have any idea on how / what to enable for LDTP
 
(what I meet error in LDTP is: 
    ldtp.client_exception.LdtpExecutionError: Unable to find window..." )
 
Thank you.

---

### Post by mcduck on 2011-10-21
Enabling any of those options should also enable assistive technologies support.

Anyway, you could also try this:
```
gsettings set org.gnome.desktop.interface toolkit-accessibility true
```

(instead of running the command you can also install the [dconf-tools]("apt:dconf-tools")-package and then use dconf-editor to change they key)

---

