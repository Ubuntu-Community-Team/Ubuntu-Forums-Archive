---
title: "I CANT get gdesklets woriking... :S"
date: 2004-12-13
forum: Desktop Environments
---

### Post by eKiNoX on 2004-12-13
Hi, i have tried almost everything... i moved so many things until gnome stoped working... then that i fix gnome i think is time to ask for help:

Here is the problem:

I downloaded gdesklets with Synaptic Package Manager (gdesklets, gdesklets-data)

Instalation was ok... 

Then when i used Applications > Accesories > gdesklets a taskbar appears telling me gdesklets is starting then it closes... (it was supposed to start the daemon)

I went to the console and type   gdesklets ~/desklets/mydesklet.display

and i got the following:
---------------------------------------------------------------------------------------------------------
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 73, in ?
    cmdlineparser.parse(sys.argv[1:])
  File "/usr/share/gdesklets/main/CmdLineParser.py", line 69, in parse
    admin.add_display(display)
  File "/usr/share/gdesklets/main/admin.py", line 73, in add_display
    displays = get_displays()
  File "/usr/share/gdesklets/main/admin.py", line 29, in get_displays
    config = singleton.get(ConfigManager)
  File "/usr/share/gdesklets/utils/singleton.py", line 20, in get
    _singletons[clss] = clss(*args)
  File "/usr/share/gdesklets/config/ConfigManager.py", line 24, in __init__
    migration.check_for_profiles(self)
  File "/usr/share/gdesklets/config/migration.py", line 20, in check_for_profiles
    config.copy([e], ["profiles", settings.profile])
  File "/usr/share/gdesklets/config/ConfigManager.py", line 117, in copy
    self.copy(src + [d], dest + [src[-1], d])
  File "/usr/share/gdesklets/config/ConfigManager.py", line 119, in copy
    value = self.get(*src)
  File "/usr/share/gdesklets/config/ConfigManager.py", line 60, in get
    return self.__backend.get(*args)
  File "/usr/share/gdesklets/config/GConfBackend.py", line 60, in get
    return v.get_string()
TypeError: gconf value does not contain a string.
---------------------------------------------------------------------------------------------------------

Then I command gdesklets to verify the daemon is initialized, and i got the following:

--------------------------------------------------------------------------------------------------------
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 73, in ?
    cmdlineparser.parse(sys.argv[1:])
  File "/usr/share/gdesklets/main/CmdLineParser.py", line 75, in parse
    settings.profile = admin.get_profile()
  File "/usr/share/gdesklets/main/admin.py", line 196, in get_profile
    config = singleton.get(ConfigManager)
  File "/usr/share/gdesklets/utils/singleton.py", line 20, in get
    _singletons[clss] = clss(*args)
  File "/usr/share/gdesklets/config/ConfigManager.py", line 24, in __init__
    migration.check_for_profiles(self)
  File "/usr/share/gdesklets/config/migration.py", line 20, in check_for_profiles
    config.copy([e], ["profiles", settings.profile])
  File "/usr/share/gdesklets/config/ConfigManager.py", line 117, in copy
    self.copy(src + [d], dest + [src[-1], d])
  File "/usr/share/gdesklets/config/ConfigManager.py", line 119, in copy
    value = self.get(*src)
  File "/usr/share/gdesklets/config/ConfigManager.py", line 60, in get
    return self.__backend.get(*args)
  File "/usr/share/gdesklets/config/GConfBackend.py", line 60, in get
    return v.get_string()
TypeError: gconf value does not contain a string.
--------------------------------------------------------------------------------------------------------

I downloaded 0.32 version of gDesklets and when i ran ./configure it stops and displays this:

--------------------------------------------------------------------------------------------------------
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
--------------------------------------------------------------------------------------------------------

I don't know what else to do or try, i hope someone can help me.
Thanks in advance.

---

### Post by eKiNoX on 2004-12-13
I fixed last problem and i installed from the source, the new problem is this one

------------------------------------------------------------------------------------------------------------------------
Cannot establish connection to daemon: timeout!
------------------------------------------------------------------------------------------------------------------------

---

### Post by alekandr on 2004-12-13
man its simple.. i have installed gdesklets and gdesklets-data from synaptic manager as well. 

what i do.. is press ALT + F2 and type:

**gdesklets**

then it does nothing, which is what its meant to do, next i press ALT + F2 again and type:

**gdesklets /usr/share/gdesklets/network/networkinfo.display**


by default all gdesklet sensors are stored in **/usr/share/gdesklets/***

edit:

p.s. i have not configured or changed anything from the gdesklet source, i jsut left it as is. and when i click Applications >> Accesories >> Gdesklets --it takes a few seconds and then its loaded, i get no messages say that gdesklets is running, nothing and im fine with that, i then run my command as mentioned above, wait a few seconds and click to place.. ive had no problems with it :D

---

### Post by eKiNoX on 2004-12-13
FIXED... the problem was the permissions...

sudo chmod 777 ~/.gdesklets 

then it worked fine... it creates some files while running.

:D

---

### Post by zAo on 2004-12-14
[QUOTE=eKiNoX]FIXED... the problem was the permissions...

sudo chmod 777 ~/.gdesklets 

then it worked fine... it creates some files while running.

:D[/QUOTE]
Never user 777 mate, instead, change the owner/roup-owner.

Just my 2 cents.

---

### Post by jcranwellward on 2006-07-18
I have gdesklets working but when i clicked to add the starter bar i get the following error:

Traceback (most recent call last):
  File "/usr/lib/gdesklets/factory/SensorFactory.py", line 42, in create_sensor
    os.chdir(p)
OSError: [Errno 2] No such file or directory: '/usr/lib/gdesklets/../../share/gdesklets/Sensors'

Can anyone help?

PS: Im running gnome on debian.

---

