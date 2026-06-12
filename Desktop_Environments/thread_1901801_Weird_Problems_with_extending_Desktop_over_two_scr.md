---
title: "Weird Problems with extending Desktop over two screens."
date: 2011-12-29
forum: Desktop Environments
---

### Post by Voidmage0 on 2011-12-29
I am using Ubuntu 11.10 64bit with Unity, a ATI HD4890 GPU and two 22'  screens at 1920x1080.

Yesterday I did a fresh install of Oneiric and had the screens being set as mirrors. I changed that to extended desktop, and it worked flawlessly. Then I messed around in compiz and had unity crash on me. After rebooting the screens would no longer extend the screen but mirror again. The settings would not allow me to change it back, saying that the desired screen size does not fit the virtual size available of 1920x1920. (I am using a german language ubuntu, my error message wont be literal).

I was unable to get it to work again, so I sighed and did another clean install. It worked again.
Now however I installed the driver ubuntu said would be appropriate. That worked and removed the lagginess but it also wont allow me to extend my screen now, with the same error message as in the prior install.

Using the Settings Menu that comes with the driver doesn't help (it just crashes when I hit apply), deactivating the driver doesn't either (just brings back the lag). If I change both resolutions, so that they fit inside 1920x1920 it works, but running on 800x600 is no option for me :-?

Is there a way to change the virtual size to the 3840x1080 that I need? There must be, since it worked before, mustn't it?

If there are any more pieces of info or log data that might help, just tell me, please.

---

### Post by Voidmage0 on 2011-12-29
I managed to solve this.

The problem was in the driver, I think. I ran ```
sudo apt-get install fglrx-updates
```and did a restart. Catalyst Control Center still crashes without changing anything, but in Ubuntus own screen settings I could now arrange the screens and resolutions however I want.

---

