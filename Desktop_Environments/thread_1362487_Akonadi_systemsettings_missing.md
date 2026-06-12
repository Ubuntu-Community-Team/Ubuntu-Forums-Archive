---
title: "Akonadi systemsettings missing"
date: 2009-12-23
forum: Desktop Environments
---

### Post by piedro on 2009-12-23
Hi! 

I installed KDE 4.4 Beta 2. Seems to be nice but I don't find the GUI to control all the Akonadi-Server settings. 

It should be in 
>> systemsettings >> advanced >> akonadi settings 
But it's missing. 

Is there any command to call that GUI within the console? 
Or has it been moved to somewhere else? 

plz help! 

thx, p.

---

### Post by Zorael on 2009-12-23
```
[00:33] <JontheEchidna> Zorael: upstream decided to remove the module, since basically the only thing you could do with it is break Akonadi (unless you really knew what you were doing)
```

If you really need to access it, you can manually start it by running '**kcmshell4 kcm_akonadi**' from a run box (Alt+F2) or a terminal. Alternatively, start '**akonaditray**', then right-click the tray icon and pick Configure.

---

### Post by Thalandor on 2010-01-14
Is there a bug report with that discussion somewhere?
It's hard to learn about things if you don't know they are there. This might be done to protect the 'average user' from himself, but why? There are plenty of other things that user can do wrong. Putting Akonadi Settings in the _advanced_ tab should be protection enough. In time, Akonadi will probably grow and become easier/safer to configure.

I don't like 'hidden' settings. Will we now get Tweak software to unhide these, like MS Windows users?

---

### Post by piedro on 2010-06-04
Akonadi Tray is perfect for all purposes, I see the point of not using it in systemsettings. 

thx, piedro

---

