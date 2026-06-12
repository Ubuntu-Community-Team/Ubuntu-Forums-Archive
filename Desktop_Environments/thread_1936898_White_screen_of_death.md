---
title: "White screen of death"
date: 2012-03-06
forum: Desktop Environments
---

### Post by TheOctagon911 on 2012-03-06
Greetings;

I have an eMachine 6522T w/AMD Athalon 64 +3500 chip, and ATI Radeon Xpress200G on-board graphics. I have installed 5 different versions of Ubuntu to try and resolve this, to no avail. (All clean installs).

The problem is that after logging into the desktop, upon (primarily) opening firefox, and at random moments, I get a 'white screen of death' and the machine totally locks up forcing a hard reset.

I have been researching this endlessly for the past two days now, and am getting no where. Some odd things reference it being a graphics adapter problem and tell me to install the ati catalyst drivers. The system errors out during that telling me it doesn't support my version. (???) -- these gotten directly from ATI/AMD via menu drop down and using various linux commands to identify my hardware correctly in order to do so. No amount of graphics drivers can be found that either my OS or my machine will accept.

I have also seen references to the whole 'cool and quiet' function of my machine being a cause, and to turn that off in my BIOS. Again, I cannot find anywhere in the BIOS for this function, although there is fan control features. If turned off, the fan runs full bloody speed all the time - unacceptable to the point where I couldn't even tell if that was the cause because I was afraid my motherboard was going to take flight before I got to Ubuntu to run it and find out. Even if it is, that is an unacceptable state for it to be in while the machine is running.

Neither of these two 'possible solutions' have bore any fruit, and I seriously need some help with this. I'm a bit of a linux noob, but not totally ignorant. So anything you need info-wise just please ask. I am one step away from installing XP and saying to hell with it. But I can't stand that option any more than I can not being able to find a reliable solution to this one in Ubuntu. 

PLEASE HELP!

---

### Post by y14 on 2012-03-06
ooh sorry to hear that...as much as I feel so strongly for ubuntu if it just doesn't work use a diff distro so you can keep with linux...maybe in the future with a new computer or release you can switch back to good old ubuntu!! sorry i was of no help...:(

---

### Post by TheOctagon911 on 2012-03-07
Man, that sure felt like a blow-off. So much for the "community" being willing to help. I guess its XP after all .....

---

### Post by jmanning002 on 2012-03-18
I've a very similar problem only my graphics are nVida-based onboard. When I KVM away from this machine with Firefox open, and I KVM back after several minutes, the screen is totally white. The mouse cursor moves around but I have no control and have to do a hard reset. I clean installed distro 11.04 earlier today and updated to the newest directly after that with the third-party graphics drivers that were recommended and tested by Ubuntu users. This is running on a [ZOTAC GF6100-E-E AM3 (up to 65 watt TDP) / AM2+ / AM2 NVIDIA nForce 430 MCP Mini ITX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500045") with a [AMD Athlon II X2 245 Regor 2.9GHz Socket AM3 65W Dual-Core Desktop Processor ADX245OCK23GM - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103933") cooled by a [XIGMATEK LOKI SD963 92mm HYPRO Bearing CPU Cooler bracket included I7 i5 775 1155 AMD and dual fan push pull compatible]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835233081"). This was the only heatsink/fan I could find that was low pro enough to get the top on the ITX case. I really need help and I'm a severe Linux noob so please be kind. :)

---

### Post by typhoon_tip on 2012-03-18
That's happened to me as well at times, with ATI. First of all, no panic. :guitar:

Then: did you install FGLRX proprietary video driver ? If yes, where did you do that ? From AMD/ATI website or from the Additional Driver subsystem ?

Please also post here the entire output of:
> lspci

---

### Post by typhoon_tip on 2012-03-18
> **jmanning002 said:**
> I've a very similar problem only my graphics are nVida-based onboard. When I KVM away from this machine with Firefox open, and I KVM back after several minutes, the screen is totally white. The mouse cursor moves around but I have no control and have to do a hard reset. I clean installed distro 11.04 earlier today and updated to the newest directly after that with the third-party graphics drivers that were recommended and tested by Ubuntu users. This is running on a [ZOTAC GF6100-E-E AM3 (up to 65 watt TDP) / AM2+ / AM2 NVIDIA nForce 430 MCP Mini ITX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500045") with a [AMD Athlon II X2 245 Regor 2.9GHz Socket AM3 65W Dual-Core Desktop Processor ADX245OCK23GM - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103933") cooled by a [XIGMATEK LOKI SD963 92mm HYPRO Bearing CPU Cooler bracket included I7 i5 775 1155 AMD and dual fan push pull compatible]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835233081"). This was the only heatsink/fan I could find that was low pro enough to get the top on the ITX case. I really need help and I'm a severe Linux noob so please be kind. :)

I suggest you open another thread, as NVidia and ATI issues may be totally different.

---

### Post by vab3 on 2012-05-23
I've been getting the white screen of death, but only inside of Firefox, not the entire screen.  It's after I switch to something else, but not sure what.  I've left it alone long enough to see it come back.  I'm using nVidia with Ubuntu 12.04 -- no special drivers.   For me all I have to do is close Firefox and reopen it.  Sorry I can't be more help on that -- just wanted to commiserate. 

I suggest trying chrome or opera for a while, maybe you could narrow down the problem.

---

### Post by egeezer on 2012-05-23
@TheOctagon911: In my experience, an eMachine that behaves that way has an overheating hard drive.

---

