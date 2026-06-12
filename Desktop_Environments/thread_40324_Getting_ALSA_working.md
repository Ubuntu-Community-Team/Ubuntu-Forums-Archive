---
title: "Getting ALSA working"
date: 2005-06-08
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-08
When I select "ALSA" and try to test it under the multimedia selector, It says that it cannot build the pipeline, or something to that effect. If I leave it on this setting and try to run music player, it says that it can't play because something else is using this device. 

How do you get alsa working? I ask because I saw in the volume control under devices 4 devices: the first two were unknown to me, the last two were alsa. It looked like they might correspond to my two sound devices.

Is alsa supposed to work, and if so, how do I get it to work? Will it let me select my sound card as the output instead of onboard if I want? Thanks!

---

### Post by NeoChaosX on 2005-06-08
sudo apt-get install libesd-alsa0, to start.

In fact, follow all the steps [here](http://ubuntuguide.org/#configuresoundproperly), and it should get it working.

---

### Post by Curlydave on 2005-06-08
Thanks, that worked (error free1!omg!!!); MUCH LOVE! :smile:

---

