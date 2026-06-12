---
title: "hardy regularly crashing"
date: 2009-04-04
forum: General Help
---

### Post by Greanbeens on 2009-04-04
Hi, i'm running Hardy Heron on a toshiba satellite notebook.

I installed ubuntu a few months ago and everything has been fine. Recently i purchased a wireless router and now connect to the internet wirelessly.

I don't remember this problem occuring before i got the wireless.

I use WICD as a network manager, and have the little weather report thing in my panel. 

The problem happens when i am running Azureus and leave the computer for a while, when i get back, Azureus is no longer downloading. I close it and try to reset the computer using the little power button in the top right of the panel. Sometimes it will do nothing at all, at other times it will seem to reset but hang on a blank screen and do nothing until i turn it off manually.

I used to have the system monitor bar in my panel displaying the ram usage etc, and i thought maybe that was the problem as it kept freezing too. Once removed the problem still happens. 

Sometimes i can do ctrl-alt-f1 (or whatever it is) and when i try to shutdown using the command "sudo shutdown -r +1" it hangs on a blank screen, or doesn't go to terminal at all.

I tried to include all the information i could, not sure what else will help. 

Thanks for your time :)

---

### Post by bertolo on 2009-04-04
delete that network manager and install this one:
sudo apt-get install network-manager

tell us the feedback.

---

### Post by Greanbeens on 2009-04-04
Seems to be working now, i'll post back if it crashes again.

Another question, how do i add network manger to my notification area? Azureus shows up fine when running so i know i have it enabled. 

Thanks for your help and quick reply. :KS

---

### Post by Greanbeens on 2009-04-05
Ok this time i had turned Azureus off for a while and was browsing with about 5 tabs open in Firefox.

Firefox crashed, so i clicked 'x' and had to 'force quit'. I tried to reopen Firefox, and it came up in the taskbar as "starting firefox" and then disapeared, then nothing happened. I tried clicking the power button to restart, and it gave so response. Although it did register the mouse was over it and slightly change colour. 

I ended up having to reboot the laptop manually again.

Any ideas? Any more info needed?

---

### Post by bertolo on 2009-04-05
lol. format your ubuntu , use bittorrent instead of azureus.
gl

---

