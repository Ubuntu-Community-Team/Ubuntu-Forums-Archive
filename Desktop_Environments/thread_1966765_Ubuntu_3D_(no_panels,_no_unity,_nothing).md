---
title: "Ubuntu 3D (no panels, no unity, nothing)"
date: 2012-04-27
forum: Desktop Environments
---

### Post by unnamed201 on 2012-04-27
Hello, I just installed the new Ubuntu 12.04 LTS and when I tried to go in Ubuntu 3D doesn't worked. Tried to choose Unity plugin in CCSM, didn't worked. Installed the latest nVidia driver (I'm using an onboard video card [geforce 7026/nforce 630])... still doesn't works.
I need some help to resolve this issue.

P.S.: Also, installed the updates.

Thanks.

---

### Post by unnamed201 on 2012-04-27
Bump

---

### Post by grahammechanical on 2012-04-27
What do you mean "didn't work?" In what way did it not work?

Did you log out and then select the Ubuntu session from the login screen? And did you then find that the desktop that loaded was Ubuntu 2D?

CCSM is not installed by default. We have to install it through the Software Centre and the Ubuntu Unity Plugin is enabled by default and cannot be disabled.

So, in 12.04 we do not need to choose the Unity Plugin. It is already chosen for us when we have activated a proprietary video driver and installed CompizConfig Settings Manager.

Even if we have installed CCSM it will not have any effect if we are in a Ubuntu 2D desktop session. We need to be in Ubuntu (= Unity 3D) in order to see any result from making adjustments through CCSM.

At the log in screen click on the Cog icon and see what sessions you have available. Ubuntu will always load into the last used desktop session unless we select another kind of session.

By the way we can now (in 12.04) make some adjustments to Unity through System Settings>Appearance. We might not need to install CCSM.

Regards.

---

### Post by unnamed201 on 2012-04-28
When I log in I choose "Ubuntu", then the screen becomes black then the wallpaper shows, but after that nothing... can't do anything (only to move my mouse).

Edit: I installed an older nvidia driver (295.33) which seems working quite well. It lags sometimes..

---

### Post by Frogs Hair on 2012-04-28
When the wallpaper appears select Ctrl + Alt + F1 . Enter the user name in lower case and password when prompted. 

Wait until  options appear and the user name appears at the bottom . Run the following command ```
unity --reset
``` You may see some errors when you run the command, so read what they say.

Wait until the command runs and your name appears again. Use Ctrl + Alt + F7 to exit tty. If the launcher doesn't appear right away just wait a few minutes.

---

