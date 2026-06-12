---
title: "K7-smp doesn't work for me"
date: 2006-06-17
forum: Desktop Environments
---

### Post by digimars on 2006-06-17
OK, I have been at this for about 6 hours now.

I have an AMD X2 4400+ dual core processor.  I have been trying to use the k7-smp kernel so that I can actually use both of my cores.  I went into synaptic package manager, and of course it automatically chooses all of the latest pieces needed, including the appropriate restricted modules (I have 2 7800GTX's in SLI mode, so I need the Nvidia drivers). 

It all downloads and installs fine (the kernel that it defaults to download is 2.6.15.25-k7).  But after about 2-5 minutes of use after I boot into this kernel and log in, my entire computer locks up.  Mouse doesn't move, keyboard shortcuts don't respond.  I have to manually reboot with the power button.  Reminds me of the days of Windows 3.1.

So I thought that I would step it back and get the previous kernel (2.6.15-23-k7).  But when I try to download it, synaptic wants to automatically put all of the latest software with it that depend on the newer kernel.  I couldn't get it to cooperate, so I figured, what the hell, I'll try it.

I reboot, choose the older kernel, and after the Ubuntu loading screen, I get the X failure screen telling me that it couldn't start X.  I figured that this was because the restricted modules wanted to work with the newer kernel and not this one.  

So I reboot again, this time to the newer k7 kernel (2.6.15-25-k7) only to find that after the Ubuntu loading screen, nothing gets sent to my monitor.  My LCD power light goes orange dictating that it is no longer recieving a signal from my video cards. 

The only way I can work in Ubuntu is to use the latest 386 kernel, and that sucks because I'm running on only half of my physical cpu hardware.

Is there a better way to do this?  I've tried the sudo apt-get, but it does the same exact thing as synaptic, getting all of the latest stuff, not letting me have anything older.

Suggestions?

---

