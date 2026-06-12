---
title: "Unity refuses login to my personal account"
date: 2011-12-27
forum: Desktop Environments
---

### Post by SeaKing on 2011-12-27
Hey,
I hava a strange problem. Yesterday I worked on ubuntu and at first skype broke and after that my whole desktop envionmente, all Panels, Unity Launcher, everything disappered but the wallpaper. CLI did work quiete well. After rebooting via CLI I got the normal Unity Login Screen, but if I tried to login, Unity acceps password but the screen becomes black and the loginscreen will be reloaded, no login. But CLI login still works. Now I tried to log in as Guest and? IT WORKED!? Unity loads fine... ](*,)
I tried unity --reset but it exited with errors.

Can anyone help?

---

### Post by grahammechanical on 2011-12-27
It would be useful if you posted those error messages that appeared when you ran unity --reset. Don't you think? It might help someone on the forums to give advice that is better than a guess.

Oh, by the way, your title is incorrect. Your log in is being accepted by the log in manager (GDM if 11.04. LightDM if 11.10) but the log in manager is failing to pass control over to the desktop environment. Perhaps the settings for the deaktop environment have become corrupted. This is my guess. You may need to re-install Compiz. Again, I am guessing.

Regards.

---

### Post by SeaKing on 2011-12-27
Error Message:

```
$sudo unity --reset
WARNING: no DISPLAY variable set, setting it to: 0

(process:1745): GConf-Warning **:Client faild to connect to the D-BUS deamon:
//bin/dbus-launch terminated abnormally with the following error: No Protocoll specified
Autolaunch error: X11 initialization failed.

Traceback (most recent call last):
  File "/usr/bin/unity", line 213, in <module>
    reset_unity_compiz_profile()
  File "/usr/bin/unity", line 84, in  reset_unity_compiz_profile
    except (GError, AttributeError), e:
Name Error: global name ''GError is not defined
```If I try to kill process 1745 the system tells me that there is no such PID

btw I logged in with my Laptop running the same system.

---

