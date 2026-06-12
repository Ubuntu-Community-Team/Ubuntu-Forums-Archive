---
title: "Parallels Workstation Installation Help"
date: 2005-12-22
forum: General Help
---

### Post by natefish on 2005-12-22
Has anyone been able to install the Parallels Workstation on Breezy? If you have can you provide some insight into what you did? I have been able to get the linux source and headers installed but now the error log is stating that "C compiler cannot create executables". I have GCC 4.0, 3.4, and 3.3 installed so I'm not sure where the error is coming from.

---

### Post by Ixtok72450 on 2006-01-01
I am also interested in this, I have not got even that far. I am having trouble adding the kernel-source.

---

### Post by clayton on 2006-01-06
I just installed it tonight, and it starts up fine.  I had to apt-get install linux-source and linux-headers before the installer would complete successfully. I have to wait until tomorrow to actually run the VM because the trial period starts then, and the registration key won't take unless the trial period has started - kind of strange that it wasn't effective immediately.

Clayton

---

### Post by Ixtok72450 on 2006-01-08
I tried the apt-get linux-sources and linux-heders and it appeared that something loaded but using the Parallels-config command gives me an error that the kernel source needs to be loaded. I have not been able to find mine. My kernel is 2.6.12-8-386.   I have found plenty of others but not mine. I think that this is the stumbling block.  I have posted another thread asking for help finding this kernel-header, Any more ideas?

Thanks
Ixtok

---

### Post by JAwuku on 2006-01-19
Clayton, could you please tell us what steps you undertook to install Parallels Workstation? I've too been struggling to install it, even having all the kernel sources and kernel headers installed.

Any feedback would be much appreciated,

Jason

---

### Post by takayuki on 2006-06-21
did anyone get Parallels installed?  here's a snippet from the parallels site:

************************
How can I install Parallels Workstation on Ubuntu Linux?

Parallels Workstation needs some packages, which are not installed by default for successful configuration.
The full list of commands to be issued is below:

apt-get install linux-headers-`uname &#8211;r`
apt-get install gcc
apt-get install libc6-dev
apt-get install make
apt-get install gcc-3.4
apt-get install libstdc++5
apt-get install libqt3-mt

if anyone got it running, can you tell us how it went?

thanks,

takayuki

---

### Post by utherwayn on 2006-07-03
I have gotten Parallels working my linux headers are 2.6.15-25-386

If I remember correctly I had to ensure that the latest version of my headers were installed, to get them I needed to allow the package manager to check the 'universe' package servers because the default ones were only giving me 2.4 headers.

Before that I had to install GCC I just picked the latest one from the default package servers.

Now I have parallels runnning a windows XP virtual machine ( I just couldnt get away from Photoshop CS2 and Warcraft III : Defense of the ancients heh ^^)

The only problem I am having at the moment is that I cannot seem to fullscreen mode parallels.  I believe it is probably an XOrg issue I have an ATI Radeon Mobility X700.  I guess debian doesn't care for ATI card's too much because my friend runs a Nvidia card and it sort of 'just works'.  Luckily for me the helpful people here had already posted something regarding getting ATI driver binaries to work.  Anyway that is my current problem right now.

---

### Post by lordmule on 2006-07-15
Hey takayuki, thanks for posting those package installs. It was complaining about compilation issue when I had both source and headers but after installing gcc-3.4 parallels-config was successful.

---

### Post by takayuki on 2006-07-22
for those running parallels...

is it solid and crash-free?  on my particular system, crossover office is a bit flaky.  is parallels a better alternative?  is it nearly as fast as native?

thanks

takayuki

---

