---
title: "vlc wont start"
date: 2005-10-17
forum: Desktop Environments
---

### Post by spockrock on 2005-10-17
ok I have tried this on both vlc 0.8.4 and 0.8.2 but when I try to start vlc via applications > sound & video > vlc media player, nothing happens, if I try to start it in the terminal with
$ wxvlc
or 
$vlc

I get segmentation fault, anyone know why this might be happening???

Also it seems my opengl screensavers no longer work, I did a clean install of breezy preview, but I have tried to install the nvidia drivers but no dice........

---

### Post by RAOF on 2005-10-17
When you say you tried to install the nvidia drivers, did you try:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
from the terminal?

That should get you working nvidia drivers.  You can check they're working by running "glxinfo" - if there's some "nvidia" in the output, you've got the nvidia drivers working.

---

### Post by spockrock on 2005-10-17
yes, I did do that.........
I tried the glxinfo and I got segmentation fault.........I think there is something else at fault, now..........

---

