---
title: "Toontown Rewrriten Permission Denied Error?"
date: 2015-09-22
forum: Gaming &amp; Leisure
---

### Post by Mukyuu on 2015-09-22
Hello, i am getting an error when i try to launch Toontown rewritten, Im sorta new to ubuntu so i dont know how to fix this, Can anybody help me? 

OSError: [Errno 13] Permission denied
  File "<string>", line 41, in run_launcher
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 123, in start
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 157, in enterCheckForUpdates
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 371, in enterPatch
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 201, in enterGetCredentials
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 231, in enterSubmitCredentials
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 309, in enterLoginResponse
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 345, in enterDelayed
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 359, in enterCheckQueue
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 287, in enterLoginResponse
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/fsm.FSM", line 64, in request
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/launcher.launcher", line 392, in enterLaunchGame
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/subprocess", line 710, in __init__
  File "/home/toonsec/pylauncher/build/start/out00-PYZ.pyz/subprocess", line 1335, in _execute_child

---

### Post by Mukyuu on 2015-10-03
Bump?

---

### Post by howefield on 2015-10-03
Haven't a clue about this game but in the absences of a reply, have you tried [this]("https://www.reddit.com/r/Toontown/comments/2rifln/installing_ttr_on_ubuntu/")..

> By default, the launcher that gets downloaded is marked as an executable. The engine, however, does not once it gets downloaded. To fix it simply open the launcher and wait for it to update all the files then in the same folder there is a file called engine. Right click that, go to permissions, and check executable. Alternatively you can use chmod +x on it from the command line.
No other file needs to be marked executable.

---

### Post by Mukyuu on 2015-10-03
Fixed it, Thanks!

---

