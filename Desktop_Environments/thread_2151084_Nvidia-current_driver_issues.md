---
title: "Nvidia-current driver issues"
date: 2013-06-03
forum: Desktop Environments
---

### Post by bturrie on 2013-06-03
Ever since the upgrade to Nvidia 304, I've had video problems. What I mean by unstable is that every 30 minutes or so the screen flashes as though it's searching for the correct resolution. Unless I force the resolution to 1680x1050 in xorg.conf it sometimes finds the wrong resolution. There's nothing obvious in the ~/.xsession-errors file or in the syslog corresponding to these resets. 

For now I've rolled back to and forced the 295 drivers which are solid on my system, but the rolled back version of nvidia-settings won't run either from the dash or from a terminal. Once again there's nothing in the logs. Also I don't get any errors in the terminal, nvidia-settings just doesn't open. My video card is a GTX550 ti running in an Intel Q9400 system.

Not sure where to go from here.

---

### Post by Frogs Hair on 2013-06-03
The nvidia-settings for that driver are not in the 13.04 repositories, but I don't know what version you are using . It appears from looking in synaptic that each driver has its own settings package and there is a Precise 12.04 settings package for that driver. but I see nothing newer.   [https://launchpad.net/ubuntu/+source/nvidia-settings](https://launchpad.net/ubuntu/+source/nvidia-settings)

You have a newer card than I and run the 3.13 + updates. I also don't know if you need to use Bumble Bee for that card, but I am sure somebody on the forum  uses that card . [http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

---

### Post by bturrie on 2013-06-03
Thanks for the response.

 I should have mentioned that I'm running 12.04. I did install nvidia-settings for the 295 drivers, it just would not run. I'm assuming there are other packages on my system that are too new to allow the 295 version of nvidia settings to run. I'd roll them back too if I knew what they were.

I believe that there was a major change between 295 and 304 at least with regard to how dual screens are handled. I think I also failed to mention that I have two monitors attached right now. Both work in 304; only the primary works with the 295 driver. I get the driver resets with 2 monitors or with only one on 304. No resets with 295.

Given that nvidia-settings won't run with the 295 driver it seems I need to choose between 295 with one monitor or 304 with periodic driver resets. Not sure idea which I like less. Alternative approaches I've thought about:

1. Try the experimental 310 drivers. Did that, they didn't help.
2. Perhaps I should purge all the nvidia drivers and reinstall them.
3. Another approach might be a fresh install.
4. I've also considered upgrading to 13.04 but I'm not sure that would help either. 

Of course I'd want to do a backup of my system partition before I tried steps 2 and higher. Then I might start with 2 and if that didn't work move on to 3. I'm reluctant to move away from LTS though which makes 4 a last resort. Not sure I have the time for an extravaganza like 2 and perhaps 3 right now though. Any other ideas would be welcome.

---

### Post by Frogs Hair on 2013-06-03
I don't have 12.04 installed, and it crossed my mind the 12.04.2 may no longer support the package because there was obviously  a 12.04 package. I believe I used Nvidia current on 12.04 and stating on 12.10 it was no longer the best option.

---

### Post by bturrie on 2013-06-03
Yeah, nvidia-current was originally the 295 driver, now it's the 304 driver. It's still called nvidia-current, at least in 12.04.

---

### Post by bturrie on 2013-06-07
Turns out the latest kernel update fixed the issue. Not sure that counts as "solved" though.

---

