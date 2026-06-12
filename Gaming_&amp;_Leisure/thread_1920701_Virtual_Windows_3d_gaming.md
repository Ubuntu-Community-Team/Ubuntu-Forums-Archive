---
title: "Virtual Windows 3d gaming"
date: 2012-02-05
forum: Gaming &amp; Leisure
---

### Post by DFortier on 2012-02-05
I'm not sure if this would be the right section, im looking for some information on setting Ubuntu as a host and then Win7 as a VM with 3d support. I know dual boot would be the "best of both worlds", however this isnt always an option. Example, i have a minecraft server setup for me and the kids (ubuntu based), sometimes they are playing MC and i would perfer to play something else (say borderlands). 
 
So im looking for something along the lines of parallels on the Mac, its not perfect but more than playable. 
 
So far i have tried VM Workstation and there is something funky that happens when you try to move via mouse (character spins rapidly and it is unplayable). Virtual box produces similar results.
 
Thanks for your time/advice

---

### Post by haqking on 2012-02-05
> **DFortier said:**
> I'm not sure if this would be the right section, im looking for some information on setting Ubuntu as a host and then Win7 as a VM with 3d support. I know dual boot would be the "best of both worlds", however this isnt always an option. Example, i have a minecraft server setup for me and the kids (ubuntu based), sometimes they are playing MC and i would perfer to play something else (say borderlands). 
 
So im looking for something along the lines of parallels on the Mac, its not perfect but more than playable. 
 
So far i have tried VM Workstation and there is something funky that happens when you try to move via mouse (character spins rapidly and it is unplayable). Virtual box produces similar results.
 
Thanks for your time/advice

Virtualbox is great IMO.

as for mouse issues, did you have the guest additions installed.

Cant say i have ever had a Vbox issue in terms of guest OS, as long as extensions pack and additions are installed.

And i run every OS under the sun in a VM at one time or another

---

### Post by xyzzyman on 2012-02-05
3d support is experimental still and due to the nature of how virtualization works may always be. They aren't meant for it and it's not a priority of the developers either.

---

### Post by haqking on 2012-02-05
> **xyzzyman said:**
> 3d support is experimental still and due to the nature of how virtualization works may always be. They aren't meant for it and it's not a priority of the developers either.

i agree.  That being said 3D works fine for me in my VM's and yet to have any issue to speak of.

Cheers

---

### Post by DFortier on 2012-02-05
Thanks for the feedback, ill give virtual box another try, although i beleive the safe mode install of the drivers had worked properly.

---

### Post by forrestcupp on 2012-02-06
> **haqking said:**
> i agree.  That being said 3D works fine for me in my VM's and yet to have any issue to speak of.

Cheers

Have they gotten it to where you can actually play a 3D game smoothly? Last time I messed with it (which has been a while), it was still a lot better to try to get things working with wine.

---

### Post by painejake on 2012-02-07
> **forrestcupp said:**
> Have they gotten it to where you can actually play a 3D game smoothly? Last time I messed with it (which has been a while), it was still a lot better to try to get things working with wine.

I also would be very interested to know this, Wine can be a PITA to setup be does produce some nice results.

---

### Post by DFortier on 2012-02-08
Hi all,
I tried vmware and virtual box again, making sure all drivers are loadind properly. In all modes (windows, unity and full screen) i get the same reaction. Moving the mouse just a bit cause a wild spin. 
 
I did find some more information on RPD that seems to have the same response. In the articale, they said that it would never work right because of the way the mouse's relitive position is calculated. Hopefully this is wrong........
 
I intend to keep messing around and look for a solution. For now though paralells seems to have gotten it right, maybe  i have to make a hackintosh for a host :frown:

---

### Post by Ozor Mox on 2012-02-10
I tried to run Windows XP in VirtualBox not long ago for gaming and didn't have much success. The copy protection on several games failed to validate that the disc was in the drive and the ones that worked usually then threw up errors about directX/3D/graphics drivers etc. Yes I had the most up-to-date drivers installed and 3D acceleration enabled in the virtual machine. The games I tried were Civ IV and a couple of others I can't remember.

In the end I gave up and set up a dual boot.

---

### Post by DFortier on 2012-02-18
Thanks for the reply, atleast i know its not something im doing wrong.

---

