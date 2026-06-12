---
title: "Can't customize Orta theme."
date: 2011-05-01
forum: Desktop Environments
---

### Post by dpc_90 on 2011-05-01
I've just installed Ubuntu v11.04 and Orta theme. The problem is that when I make changes in Orta Settings Manager they have no effect at all, even after I save them and unselect and select Orta Theme in Appearance Preferences. For instance, I never get the dark panel, but only the light one.

Thanks in advance for your help!

---

### Post by Copper Bezel on 2011-05-01
Curious. Did you install Orta from the PPA, or by some other method?

---

### Post by dpc_90 on 2011-05-01
I installed it direcly from the PPA, running:

sudo add-apt-repository ppa:nikount/orta-desktop
sudo apt-get update
sudo apt-get install orta-theme

I also installed emerald and xfwm4 decorations:

sudo apt-get install orta-emerald-decorators
sudo apt-get install orta-xfwm4-decorators

---

### Post by Copper Bezel on 2011-05-01
Weird. I haven't experienced that behavior, although I'm not using 11.04. Let's hope that someone else has run into this (and either has a fix or more details on the problem.) The package doesn't have any bugs listed on Launchpad (and if we can't solve the problem, you might need to report one.)

---

### Post by mexlinux on 2011-07-18
I have the exact same problem.... did you fixed it?

---

### Post by tlcstat on 2011-07-18
Greetings,
Try this for orta and more. Look for the orta theme manager in the system panel. The extra update and upgrade is just to make sure everything is installed. This is from redmondpie.com. FYI

sudo add-apt-repository ppa:webupd8team/themes
sudo apt-get update

sudo add-apt-repository ppa:nikount/orta-desktop
sudo add-apt-repository ppa:elementaryart/elementarydesktop
sudo add-apt-repository ppa:tiheum/equinox

sudo apt-get update
sudo apt-get upgrade

sudo apt-get install orta-theme orta-emerald-decorators
sudo apt-get install elementary-icon-theme
sudo apt-get install gtk2-engines-equinox faenza-icon-theme equinox-theme
sudo apt-get install faenza-icon-theme

sudo apt-get update
sudo apt-get upgrade

PS if you make changes in the orta panel you may have to put in your password a few times to save it. And it asks that you switch to a different theme and then back to orta to activate it.
tlcstat

---

### Post by Frogs Hair on 2011-07-18
I experienced strange behavior on 11.04 with the Orta  PPA . As stated above I had to enter my password many times before I was able to make changes. In the end I removed the PPA , but may try again later .

---

### Post by tlcstat on 2011-07-18
Greetings,
The changes will install correctly. I'm not sure how the installer is coded but it seems that there are multiple processes at work and each needs a password to complete. It has finished every time for me. Just make sure that when it finishes you switch to a different theme and then back to complete the process.
tlcsta

---

### Post by Frogs Hair on 2011-07-18
> **tlcstat said:**
> Greetings,
The changes will install correctly. I'm not sure how the installer is coded but it seems that there are multiple processes at work and each needs a password to complete. It has finished every time for me. Just make sure that when it finishes you switch to a different theme and then back to complete the process.
tlcstat

Thank you , I thought there may have been something wrong and got a little gun shy .

---

