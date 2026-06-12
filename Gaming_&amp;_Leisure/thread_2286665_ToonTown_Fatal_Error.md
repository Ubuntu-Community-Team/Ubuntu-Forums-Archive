---
title: "ToonTown Fatal Error"
date: 2015-07-13
forum: Gaming &amp; Leisure
---

### Post by LinuxCharms on 2015-07-13
I'm trying to install Toontown rewritten and I'm encountering an error with the launcher.

Here is the crash report:
```
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

```

I have tried going into the terminal and running as sudo, but I have had no luck.
Thanks in advance!

---

### Post by aqsalomon on 2015-08-27
Same with me! Please tell the TTR Team to fix this annoying error!!! :'(

---

