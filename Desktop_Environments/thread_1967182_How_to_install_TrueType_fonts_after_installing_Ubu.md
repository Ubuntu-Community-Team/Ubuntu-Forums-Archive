---
title: "How to install TrueType fonts after installing Ubuntu Restricted Extras without it"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Colin Keenan on 2012-04-27
After a thunderstorm ruined my upgrade to 12.04 by rebooting my computer and modem for me during the upgrade, I ended up doing a clean install of 11.10 then upgrading to 12.04.

When I installed Ubuntu Restricted Extras, I forgot to check the box that comes up having to do with TrueType fonts. When I clicked the forward button without that box checked, it warned me that TrueType fonts would not be installed, but didn't give me any way to go back and check the box.

I let the install finish, and tried removing it then re-installing, but the question about TrueType fonts won't come up again. I don't seem to have anyway to install them.

Can anyone tell me how to get TrueType fonts if they weren't installed with Ubuntu Restricted extras?

---

### Post by Krytarik on 2012-04-27
Install the package "ttf-mscorefonts-installer", preferably via Software Center or Synaptic, otherwise see here how to overcome the EULA obstacle in the Terminal:

[http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html](http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html)

Regards.

---

### Post by Colin Keenan on 2012-04-27
Thanks for the quick reply. The link you provided is out of date and does not reflect the alerts that currently occur during install. Also the terminal command given did not fix the problem. Thanks to you pointing me to ttf-mscorefonts-installer, I found the correct terminal command: sudo apt-get purge ttf-mscorefonts-installer. After that, I was able to install it and get the chance to click the check box saying I agree to whatever it is so that TrueType was installed.

---

### Post by cesarsalles on 2012-07-16
I had this same problem. Thanks for helping me to solve it.

---

