---
title: "Please help me with Compiz -Nvidia 6200 drivers. Arggh."
date: 2012-09-15
forum: Desktop Environments
---

### Post by Bullpen on 2012-09-15
I have a P4 2.4 Ghz machine with a nVidia geForce 6200 pci card, 256mb. I have tried at least 4 iterations of Mint and other Ubuntu variants, trying to find a distro that will install the proper drivers that will enable desktop effects and run compiz. 

I currently have Ubuntu installed (10.04)

I have tried enabling the additional/proprietary drivers, (all three that come up when I go to additional drivers) to no avail. I always get"desktop effects could not be enabled" 

I have, in researching the issue, also tried the following: 

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

Also to no avail. 

It would appear that some have in fact had success running compiz with this particular card. 

What do y'all think? Is there a distro that will work better? I'm using buntu 10.04 now, because I read of some accounts where folks had the 6200 working on that distro. 

Is there a procedure I am missing somewhere? Is 256mb of video memory just not enough? 

I brought the live usb stick to work, and it worked on my work pc just fine (which, granted, is newer)

I would greatly appreciate some assistance on the matter from the collective Ubuntu geeks.....

Thanks kindly!

Regards,

---

### Post by Epodx64 on 2012-09-15
Add the x-swat ppa like you did then 

sudo apt-get update

then try going to dash menu and type in jockey then download and install the Post-Release-Current nvidia driver should be 304.x 

When I had a Nvidia chipset I had a plethora of problems with the Nvidia 179-29x.x  drivers the only drivers that worked for me where the 304.x drivers honestly that chipset gave me such a hard time  with installing anything I ended up selling it It got to the point where 2D Unity wouldn't boot or even Xfce in Xubuntu.

---

### Post by Bullpen on 2012-09-15
Thx epod, -I could use an elaboration on the procedures outlined above... Still pretty new to the Os ( as you probably surmised)

I may give this a go and see if i cant break my install. ( not for lack of good instruction- do appreciate the hints. I just have a way of messing things up...) Failing that, i think perhaps rather than struggling with this, I will be looking for a more user friendly video card. Life's too short to fool with sort of thing when options to solve the problem with a small investment exist. 

Recommendations welcome. If there are some known options in the pci graphics card department that do not require some magical combination of voodoo, the force and a Torvalds-like knowledge of the command line, that would be super dee duper.

---

### Post by Bullpen on 2012-09-16
Bump. Managed to get the 304.43 version of the nvidia drivers installed, thanks to a little research and the script provided by people much smarter than myself at: 
[http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/](http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/)

No avail. Still get "Desktop effects could not be enabled". 

Is it the chipset or the amount of memory on the card that is the problem? 

Does someone have a recommended PCI card that would run compiz without the hoop jumping?

---

