---
title: "Can't access administrative settings when logged in remotely through xdmcp on Hardy"
date: 2008-05-26
forum: Desktop Environments
---

### Post by lokster on 2008-05-26
I have posted this as a bug report on launchpad.net, but there is still no fix for it there. Sorry if it is in the wrong forum.
Here is my problem:

I am using Hardy 8.04 with Gnome, and I have enabled remote login from gdmsetup -> "Remote" (Plain, with face browser). When I login from a windows machine using Xming, the "Unlock" button on all settings that require administrative privileges is disabled.
Also, when I try to open any of the disk drives from Nautilus, the error message appears:
"Can not mount volume
Error org.freedesktop.DBus.Error.AccessDenied.

Asecurity policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal"

In 7.10 I didn't had any of these problems with gdm set up in the same way, and using Xming to log in from windows machine.

Please, any advices on how to fix this?

---

### Post by Aearenda on 2008-05-26
Look in System->Administration->Authorisations, and find the settings for the actions you want to accomplish. I suspect when local you are being implicitly authorised to do things, but when remote it needs to be explicit. Can't say I've tried this yet!

---

### Post by lokster on 2008-05-26
Thanks, but unfortunately this does not work. In "Authorizations" I have changed all Implicit authorizations for "Anyone" and "Console" to be the same as for "Active Console".
Especially "Mount file systems for internal drives" is set to "Yes" for "Anyone", "Console" and "Active Console". But still, I can't mount my drives, and  the "Unlock" button on all Administrative programs is disabled, when logged in remotely through XDMCP.

:edit

After remote logout/login the "Unlock" button is Active everywhere, and I can access administrative settings. But still, I can't mount my drives.

:another edit

I forgot to mention that when logged in remotely through XDMCP on Hardy, the system works a lot slower compared to when working remotely through XDMCP on Gutsy. When I click the "Shutdown" button in GNOME, it takes about 10 seconds for the shutdown dialog to appear.

---

### Post by mooncaptain on 2008-06-22
As of  22 Jun 08 I have all the latest updates. I have had the same problem as described. I also changed the implicit authorization settings, specifically for "Mount file systems from internal drives". This didn't help. However, I explicitly gave my user login rights through an active session whether or not logged in through the console. This did the trick at least with an active login.  I am hoping that local services such as vm server can access the internal drive.

---

