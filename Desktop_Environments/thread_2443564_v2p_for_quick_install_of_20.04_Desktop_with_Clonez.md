---
title: "v2p for quick install of 20.04 Desktop with Clonezilla or Rest-and-Recover?"
date: 2020-05-17
forum: Desktop Environments
---

### Post by bob15 on 2020-05-17
Hi folks-

I work in IT and have been using Ubuntu desktop for personal productivity for years. My business is time constrained (SLAs) so time is tight during normal business hours (and somewhat outside too). I have one main workstation.

I need to do a fast turnaround of a fresh install of Kubuntu 20.04 with everything I currently have installed in 18.04.4. Unfortunately I have a TON of "extras" - flatpaks, appimages, snaps, lxd containers, extra debs, extra python modules, and MORE.

I am thinking of reinstalling all of it in a fresh Kuduntu 20.04 VM as time permits, then use either Clonezilla or Rest-and-Recover and do a "v2p" onto my primary hardware. I do have a separate rather beefy desktop available with VirtualBox. My "data" is separated from the OS/Ubuntu on separate disks.

Unfortunately I do not have test hardware :(

Has anyone done this?
What kind of issues should I expect to have?

I do use LVM quite a bit for things like system disk + data disk + for lxd containers.

Also the target hardware has an Nvidia GPU (to drive large resolution monitors) so I suspect at least one issue might be drivers.

I have googled v2p but only found rather dated material and nothing too specific (although I could have missed something important).

If anyone has attempted something similar, I would appreciate hearing any experiences and/or potential issues ... and especially, if this would work, what issues might crop up *after*.

Lastly, I am open to alternatives if anyone has any too.

TIA,
BobC

---

### Post by TheFu on 2020-05-17
i just moved a 16.04 desktop to a 20.04 desktop, both inside VMs.  Lots and lots of packages deprecated and apt-mark failed to install those that do exist on the new system.  i have a list of all manually installed packages.  Looks like i get to go through them daily and try a pageful at a time.
Make lists of the flatpak and snaps installed.
Copy over the appimages
all the manual .deb files are liabilities.  Those are gonna cause issues if they haven't already.  
No clue how to do the lxd containers. Thought lxd v4 includes a backup and restore capability, but those guys love zfs, so if you are using thin LVM, it probably doesn't work.

For a system that critical, why not go 100% virtual for most things and keep the base OS on the actual HW as minimal as possible?  My main desktop is a VM.  When the 20.04 migration is done, I&#8217;ll shutdown the other VM and schedule deletion for 60 days later via at.   There are all sorts of great reasons to use VMs.

---

