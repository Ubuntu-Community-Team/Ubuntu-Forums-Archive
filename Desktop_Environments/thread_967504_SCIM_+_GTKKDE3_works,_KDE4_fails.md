---
title: "SCIM + GTK/KDE3 works, KDE4 fails"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Urzumph on 2008-11-02
Hi,

I have been having some trouble with Japanese input with KDE4 applications. GTK (Firefox) apps and KDE3.5 apps (Konversation) work just fine. KDE4 apps konqueror, kwrite, etc (and OpenOffice for some reason) don't work.

My configuration is set up correctly, as best as I can tell.

```
christian@Piro:~$ im-switch -l
Your input method setup under en_AU locale as below.
=======================================================
The configuration "/home/christian/.xinput.d/en_AU" is defined as a link pointing to                                                                            
scim-bridge                                                                     
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
default default-xim none scim scim-immodule skim th-xim
=======================================================
```

Despite im-switch saying the scim-bridge module is the default method, opening an app such as Konqueror and gong to "select IM" shows XIM is selected by default. After changing it to scim-bridge, I can change input-modes with Ctrl-Space, like I can in GTK/KDE3 apps. However, after changing the input mode to Anthy/Japanese it refuses to input any characters until the mode is changed back to English.

This is particularly annoying, since KDE's useful Japanese dictionary tool, Kiten, is KDE4.

Anyone have any ideas?

I have the following scim packages installed:
```
christian@Piro:~$ dpkg -l scim* | grep ii
ii  scim                                       1.4.7-3ubuntu10                                      smart common input method platform
ii  scim-anthy                                 1.2.4-1.1                                            SCIM IMEngine module for Anthy
ii  scim-bridge-agent                          0.4.14-2ubuntu5                                      IME server of scim-bridge communicate with S
ii  scim-bridge-client-gtk                     0.4.14-2ubuntu5                                      IME server of scim-bridge communicate with S
ii  scim-bridge-client-qt                      0.4.14-2ubuntu5                                      IME server of scim-bridge communicate with S
ii  scim-bridge-client-qt4                     0.4.14-2ubuntu5                                      IME server of scim-bridge communicate with S
ii  scim-gtk2-immodule                         1.4.7-3ubuntu10                                      GTK+2 input method module with SCIM as backe
ii  scim-modules-socket                        1.4.7-3ubuntu10                                      socket modules for SCIM platform
ii  scim-qtimm                                 0.9.4-2ubuntu3                                       SCIM context plugin for qt-immodule
```

---

### Post by Urzumph on 2008-11-02
Update:

I went into System Settings and told it to install Japanese language support. It went and installed a bunch of packages, but didn't give me the opportunity to find out what they were.

Now:
After force-changing the input method to SCIM in KDE4 apps input now works in Japanese. Random parts of the System settings dialog seem to be in Japanese, despite the default language being set to US English.

I would still like SCIM to be the default input method for KDE4 though. Oh, and Openoffice still doesn't work either :(

---

### Post by Urzumph on 2008-11-04
Hmm, some more things I discovered:

I'm guessing the fact that some things seem to be in English and others in Japanese is caused by:
[email]christian@Piro:~/.kde[/email]/share/config$ echo $LANG
en_US.UTF-8
[email]christian@Piro:~/.kde[/email]/share/config$ echo $LANGUAGE
ja

Does anyone know what file sets $LANGUAGE and where I can change it?

I also tried KOffice as an alternative to OO for Japanese - parts of it work, parts of it don't. I suspect this is a KOffice bug, not an issue with my setup

---

