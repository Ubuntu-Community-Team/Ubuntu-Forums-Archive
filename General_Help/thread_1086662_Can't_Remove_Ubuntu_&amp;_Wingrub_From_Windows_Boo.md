---
title: "Can't Remove Ubuntu &amp; Wingrub From Windows Boot Manager"
date: 2009-03-04
forum: General Help
---

### Post by pretenderzl on 2009-03-04
I've read a similar question here:
[http://ubuntuforums.org/showthread.php?t=829466](http://ubuntuforums.org/showthread.php?t=829466)

and then go through an excellent long article about BCDedit:
[http://technet.microsoft.com/en-us/l.../cc721886.aspx](http://technet.microsoft.com/en-us/l.../cc721886.aspx)
but only find it useless, I've got a rare problem...

My problem is I've tried several times to install Ubuntu but failed. Resulting in adding two more useless optionins in the Windows boot manager, one is Ubuntu, the other is Wingrub. 

Either of them won't run, but how do I remove them? 
I have two hard drive, two system: Windows XP   Windows 7
when I use bcdedit to edit Windows Boot Configuration Data, there's no "Ubuntu" or "wingrub",
so I really don't know use command-line "bcdedit /delete" to delete what or which {ID}

If you know how to deal with this problem leave me a message plase, thank you so much!
mail me is fine too. [email]pretender_zl@hotmail.com[/email]

---

### Post by pretenderzl on 2009-03-04
here is the Boot Configuration Data:

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {fa81845e-07b7-11de-8c1a-99c28aeb518d}
displayorder            {ntldr}
                        {current}
toolsdisplayorder       {memdiag}
timeout                 15

Windows Boot Loader
-------------------
identifier              {fa81845c-07b7-11de-8c1a-99c28aeb518d}
device                  ramdisk=[\Device\HarddiskVolume1]\Recovery\fa81845c-07b7-11de-8c1a-99c28aeb518d\Winre.wim,{fa81845d-07b7-11de-8c1a-99c28aeb518d}
path                    \windows\system32\winload.exe
description             Windows Recovery Environment
inherit                 {bootloadersettings}
osdevice                ramdisk=[\Device\HarddiskVolume1]\Recovery\fa81845c-07b7-11de-8c1a-99c28aeb518d\Winre.wim,{fa81845d-07b7-11de-8c1a-99c28aeb518d}
systemroot              \windows
nx                      OptIn
detecthal               Yes
winpe                   Yes

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=E:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {fa818460-07b7-11de-8c1a-99c28aeb518d}
recoveryenabled         Yes
osdevice                partition=E:
systemroot              \Windows
resumeobject            {fa81845e-07b7-11de-8c1a-99c28aeb518d}
nx                      OptIn

Windows Boot Loader
-------------------
identifier              {fa818460-07b7-11de-8c1a-99c28aeb518d}
device                  ramdisk=[E:]\Recovery\fa818460-07b7-11de-8c1a-99c28aeb518d\Winre.wim,{fa818461-07b7-11de-8c1a-99c28aeb518d}
path                    \windows\system32\winload.exe
description             Windows Recovery Environment
inherit                 {bootloadersettings}
osdevice                ramdisk=[E:]\Recovery\fa818460-07b7-11de-8c1a-99c28aeb518d\Winre.wim,{fa818461-07b7-11de-8c1a-99c28aeb518d}
systemroot              \windows
nx                      OptIn
detecthal               Yes
winpe                   Yes

Resume from Hibernate
---------------------
identifier              {fa81845e-07b7-11de-8c1a-99c28aeb518d}
device                  partition=E:
path                    \Windows\system32\winresume.exe
description             Windows Resume Application
locale                  en-US
inherit                 {resumeloadersettings}
filedevice              partition=E:
filepath                \hiberfil.sys
pae                     Yes
debugoptionenabled      No

Windows Memory Tester
---------------------
identifier              {memdiag}
device                  partition=C:
path                    \boot\memtest.exe
description             Windows Memory Diagnostic
locale                  en-US
inherit                 {globalsettings}
badmemoryaccess         Yes

Windows Legacy OS Loader
------------------------
identifier              {ntldr}
device                  partition=C:
path                    \ntldr
description             Windows XP

EMS Settings
------------
identifier              {emssettings}
bootems                 Yes

Debugger Settings
-----------------
identifier              {dbgsettings}
debugtype               Serial
debugport               1
baudrate                115200

RAM Defects
-----------
identifier              {badmemory}

Global Settings
---------------
identifier              {globalsettings}
inherit                 {dbgsettings}
                        {emssettings}
                        {badmemory}

Boot Loader Settings
--------------------
identifier              {bootloadersettings}
inherit                 {globalsettings}
                        {7ff607e0-4395-11db-b0de-0800200c9a66}

Inherited Settings (20200003)
-----------------------------
identifier              {7ff607e0-4395-11db-b0de-0800200c9a66}
custom:250000f3         0
custom:250000f4         1
custom:250000f5         115200

Resume Loader Settings
----------------------
identifier              {resumeloadersettings}
inherit                 {globalsettings}

Device options
--------------
identifier              {fa81845d-07b7-11de-8c1a-99c28aeb518d}
description             Ramdisk Options
ramdisksdidevice        partition=\Device\HarddiskVolume1
ramdisksdipath          \Recovery\fa81845c-07b7-11de-8c1a-99c28aeb518d\boot.sdi

Device options
--------------
identifier              {fa818461-07b7-11de-8c1a-99c28aeb518d}
description             Ramdisk Options
ramdisksdidevice        partition=E:
ramdisksdipath          \Recovery\fa818460-07b7-11de-8c1a-99c28aeb518d\boot.sdi

---

