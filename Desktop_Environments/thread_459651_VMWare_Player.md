---
title: "VMWare Player"
date: 2007-05-30
forum: Desktop Environments
---

### Post by ryanVickers on 2007-05-30
Ok, after many other troubles, I finally got it "working". By this I mean it starts, which is big for me, and it looks like it's going to be good, but I have absolutely no clue how it works.  For now, however, all I need to know is what "virtual machine files (.vmx)" are, and where I can find one.  I assume it's the file that simulates a windows (or other OS) environment, kind of like a drive in one file I guess (correct me if I'm wrong).  But where might I find one/make one to get started?

FYI I have a legal and working copy of Windows XP Home installation disk if this helps in anyway
Please help!  A few tips like this to get me started is all I'll need most likely.  I don't need anything complex, like USB/Firewire/internet/etc. for it, just working environment!

---

### Post by TomMK on 2007-05-31
OK, I was messing with VMware player last night so I'll tell you what i did.

In Windows:
I used VMware Workstation (i believe the 30 day trial will be ok) to create a new virtual machine. I installed windows xp on that virtual machine. Once the virtual machine has booted up, press the "VM" menu and then "Install VMware Tools". You need to do that to get good graphics preformance when you're running it in Ubuntu. Now shutdown the virtual machine, and close VMware Workstation. Locate the virtual machine folder, usually in "My Documents\My Virtual Machines", and make a copy of it (I burned it to a DVD-R) so that you can access it in Ubuntu.

In Ubuntu:
Copy your virtual machine to your home folder. Install VMWare Player (it sounds like you already have) by typing "sudo apt-get install vmware-player" into the terminal. Open VMware Player from the Applications menu. Locate the virtual machine in your home folder and run it.

Job done. Does that help?

---

### Post by ryanVickers on 2007-05-31
previous post:
> Do you know if there is a way to do it completely in ubuntu - I could install windows, but I REALLY don't want to.  That's why I'm getting this - to avoid windows (to a certain extent) :)

p.s. I/you can access windows files from ubuntu without having to burn a disk, transfer it, etc.

Well, I went [here]("http://www.easyvmx.com/") and it's incredible - it's working perfectly!  I'm just wondering if there is a way to get it to run a little faster (the whole system runs at about 15 fps with nothing difficult open)

Overall though, I'm pleased for now :)

---

### Post by TomMK on 2007-06-01
> **ryanVickers said:**
> the whole system runs at about 15 fps with nothing difficult

Did you install VMware Tools? I had the same performance problems before I installed VMware tools, now its fine.

---

### Post by ryanVickers on 2007-06-01
> Once the virtual machine has booted up, press the "VM" menu and then "Install VMware Tools".
No, not yet - I couldn't find such a menu.  Is there other ways to do that?

---

### Post by ryanVickers on 2007-06-01
Never mind, I found another easy way, it's great now, this will be really good!  Thanks for your help!

Update:  Now with the VM Tools, it's much better than it was, but it's still pretty bad!  For example, I remember a long time ago, I was using a 486 with win95 and it ran the old pinball game fine, but now on my 3 Ghz duel core AMD it runs at about 30% of what it should be doing!!!  Any ideas?

---

### Post by ryanVickers on 2007-06-04
Ok, I made another VM with the experimantal 3D accel. enabled, and the pinball works ok now :p

I've still noticed it's slow without any good reason (no point I can see), but it's fine for what I do!

---

