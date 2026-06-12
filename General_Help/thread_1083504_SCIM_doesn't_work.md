---
title: "SCIM doesn't work"
date: 2009-03-01
forum: General Help
---

### Post by newgalois on 2009-03-01
Hi,

I'm using Ubuntu 8.10 and would like to use SCIM to type Vietnamese. I have enabled the Vietnamese language support, checked the option to "enable typing complex character".

Now SCIM run when I log in, but I cannot do anything with it. Nothing happens when I left click on the applet or press the trigger keyboard shorcut. Right click does allow me to config or exit SCIM though.

Is there anything I can do?

Here are the results of "locale", "im-switch -l" and "cat /etc/scim/global":
--locale----
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"

--im-switch -l ----
Your input method setup under en_US locale as below.
=======================================================
The configuration "~/.xinput.d/en_US" is defined as a link pointing to
scim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is auto.
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim none scim scim-bridge scim-immodule skim th-xim 
=======================================================

--cat /etc/scim/global----
/SupportedUnicodeLocales = en_US.UTF-8
/DefaultPanelProgram = scim-panel-gtk
/DefaultConfigModule = simple
/DefaultSocketFrontEndAddress = local:/tmp/scim-socket-frontend
/DefaultSocketIMEngineAddress = local:/tmp/scim-socket-frontend
/DefaultSocketConfigAddress = local:/tmp/scim-socket-frontend
/DefaultPanelSocketAddress = local:/tmp/scim-panel-socket
/DefaultHelperManagerSocketAddress = local:/tmp/scim-helper-manager-socket
/DefaultSocketTimeout = 5000

---

### Post by brianobush on 2009-06-08
I too have the same problem with SCIM/anthy. I cannot switch to Japanese input and the tray icon does not respond to right-click for engine selection. The left click of tray icon works and allows to exit/config/etc. Anyone?

I am using 9.04, but the problem existed before I upgraded (from 8.10). I recall hitting "hide toolbar" once, while it was working. Sometime after that (maybe immediately?!) it stopped working.

Thanks

---

### Post by natuwes1968 on 2009-07-27
Hello,

On my computer the same problem since two weeks or so. I am using (K)Ubuntu 9.04 but I can not use scim or skim anymore since some recents updates for Ubuntu. I can alter the settings though, but can not type Chinese characters anymore. It worked when updating from 8.10 to 9.04. Re-installing scim or skim does not solve the problem either. So now I always have to use windows again to type in Chinese. Who can solve this problem?

natuwes1968

---

