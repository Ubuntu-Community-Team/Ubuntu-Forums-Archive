---
title: "Upgrading to Ibex"
date: 2009-03-07
forum: General Help
---

### Post by jamesdcarroll on 2009-03-07
I read the FAQ on new bugs and there didn't seem to be anything that would effect my system so I started the upgrade process.  I got this message:

[B]Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 8.10.

Do you want to continue?[/B]

I do use the ATI proprietary drivers, but not AMD ones and I did find 'fglrx' drivers in Synaptic as installed. I don't care too much about compiz and have it turned off ("Visual Effects = None") as far as I can tell.

My card is an ATI Radeon 9700 Pro.

Couple of questions:
If I press forward, will there be any way to revert? 
If I don't use the compiz effects, can I just use the free drivers?
What might be the best way forward? I wouldn't mind playing with all the eye candy but system stability is the most important thing above all else. 


Hardy was my first version of Ubuntu and I spent a week trying to get it to work and almost gave up and went back to windows. I would prefer to use free drivers and have this not be an issue, but IIRC my system was unstable and slow without them. I really don't want to go through that again. 

Thanks for any insights that you might have.

---

### Post by Svensk023 on 2009-03-07
1. I would fresh install Ibex instead of upgrading, but give upgrade a try if you dont use a separate /home partition 
2. there is no way to revert without a fresh install back to hardy.
3. You can use free drivers but just go to [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") 
run:
sudo sh
 with the .sh file in terminal to install it, then just use the automatic installation function and it will do everything for you.
it should work fine, i have 2 ATI Radeon 3870's and i havent had any problems in Ibex with the proprietary drivers.

---

