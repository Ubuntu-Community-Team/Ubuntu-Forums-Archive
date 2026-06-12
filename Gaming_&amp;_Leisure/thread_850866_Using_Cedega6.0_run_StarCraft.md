---
title: "Using Cedega6.0 run StarCraft"
date: 2008-07-06
forum: Gaming &amp; Leisure
---

### Post by louis3234 on 2008-07-06
Hi guys. I'm not exactly sure how to use Cedega6.0
When I installed StarCraft then run the program, at first, the screen wasn't right. The image was not at the center of the screen. I thought it's the resolution problem. So I changed it to 1024x768. When I tried to run it again, this time it appears as a window, just black. Then the program froze. I tried 800x600, and default the whole setting, but Starcraft just appear as a window with nothing in there.
how do I solve this problem?

---

### Post by kdorf on 2008-07-06
Starcraft should be run at 640x480. I don't know Cedega very well, but my guess is you'd need to run Starcraft in a virtual desktop with a resolution of 640x480.

---

### Post by louis3234 on 2008-07-06
Alright..Thanks for your help, it worked. But the mouse seems bit laggy when there are too much things going on. How can I fix that?
And, I'm not allowed to log on battle.net. When I click on it, it just jump back to where i started.

---

### Post by kdorf on 2008-07-06
If the Battle.net issue is a Wine/Cedega problem, there would likely be some terminal output when you try to connect. Run Starcraft from the terminal and see what you get after trying to connect to B.net.

Also, look at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149) and apply the registry tweak for DirectDrawRender to see if that helps with the mouse or other general slowness.

---

### Post by louis3234 on 2008-07-06
Thanks! The slowness was cured! But how do I launch Starcraft using Cedega in terminal?

---

### Post by kdorf on 2008-07-06
You need to know the command to execute to Cedega. From a quick Googling it looks like it is just cedega. You also need to know where Starcraft is located. Note that you can use either a Unix-style path or a Windows path. The command should look something like this:


```
cedega "C:\Program Files\Starcraft\starcraft.exe"
```

Just make sure that is the actual path to Starcraft, as I don't know offhand what that is. You can check in the Cedega settings directory in your home (probably .cedega) and see where it is installed.

Hope that helps.

---

### Post by louis3234 on 2008-07-07
well...When I tried to launch Starcraft using cedega, the image wasn't in the center of the screen...Also, the terminal report: ```
RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
```
What is that?

---

### Post by louis3234 on 2008-07-07
Alright...The battle.net problem was solved. But still, I got new problems. When I launch directly from the Cedega manager, sometimes it won't launch, I can only hear the sound and i can see Starcraft is proceeding, but nothing happens besides music. When I launch it from terminal, it success evertime, but the image wasn't displayed in the middle of the screen(for clearer description, please look in the attachment).
Any ideas will be acceptable, I REALLY want to play Starcraft!!!

[EDIT]Well, when I tried to use terminal launch Starcraft again, new error message, wish this explains something:```
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
process 11805: arguments to dbus_connection_unref() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2610.
This is normally a bug in some application using the D-Bus library.
process 11805: arguments to dbus_connection_flush() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3339.
This is normally a bug in some application using the D-Bus library.
```

---

### Post by louis3234 on 2008-07-09
Anyone? I really have no idea what is it.

---

