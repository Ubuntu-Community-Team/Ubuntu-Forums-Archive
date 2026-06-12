---
title: "Moblin on regular Ubuntu installation?"
date: 2009-09-30
forum: Desktop Environments
---

### Post by alcatraz on 2009-09-30
Hello everyone,

I wanted to ask if it is possible to install the "Moblin" interface on a regular Ubuntu installation?!

Best would be if there would be a kind of "switching" between the regular and Moblin interface. (killing old window manager and starting the moblin one?).

Any ideas? I saw some moblin packages in the repository, but I don't know how to use it.

---

### Post by afonteijn on 2009-10-10
I agree with alcatraz, it would be great if we could install moblin packages on top of a normal ubuntu installation. Specifically, because the normal moblin installation (and I belief that also goes for the the Ubuntu Karmic Moblin Remix) doesn't run on non-Intel hardware (both proc and video card). So running it on an Ubuntu installation that does recognize that type of hardware would be great!

Btw: I have been trying to install the moblin packages on top of Opensuse... somehow I ran in a lot of dependency problems... but I understand this might be our best shot on running moblin.

---

### Post by sloggerkhan on 2009-10-10
I don't know about moblin, but the karmic netbook remix is a metapackage and has a control panel item to switch between desktop styles. So I think it may work on other machines.

---

### Post by roblloyd on 2009-10-13
From what I understand so far, moblin, because it is developed by intel, will not be ported to any processor achitecture other than the atom processor. However, i believe moblin is open source. This means it's only a matter of time before the bugs in the source code are ironed out so it works on other distributions. 

I must say the concept of the desktop interests me. I could see this type of interface on a big plasma screen and my wiimote doing all of the work as a pointing device.

Now i feel guilty that i wouldn't even know where to start helping develop it and stop it being so buggy, even on x86 processors, let alone 64 bit ones. I did see mention that a lot of the problems lie in the grapics end of things though

Looking forward to developments though

---

### Post by afonteijn on 2009-10-13
Hi roblloyd, thanks for your reply and insights. You might be right. I was just looking at the [moblin website from opensuse]("http://en.opensuse.org/Moblin"). Here you can install the moblin ui into opensuse. I noticed that other architectures are not being mentioned. However, I can not find a statement that says that it is impossible to install on x86 hardware either. 

In an [article at linux world]("http://www.linuxworld.com/news/2009/050709-novell-throws-support-behind-moblin.html") Guy Lunardi, director of client preloads for Novell said that he will focus "on optimizing Moblin for Atom and other x86 chips, not ARM." Followed by "We are very committed to the x86 architecture." So I guess that means that this project is also meant for other intel and AMD x86 proc.

Anyway, did anyone get the opensuse / moblin combo to run on a non-atom proc?

---

### Post by snowpine on 2009-10-14
Moblin, the distro, is specific to Intel processors.

Moblin, the user interface, runs on anything the core distro runs on. So "Ubuntu Moblin remix" (or whatever it's called) should run on anything that can run Ubuntu.

---

### Post by roblloyd on 2009-10-14
@snowpine strangely, no. UMR is a no go on both my dell and Packard Bell Laptops. The error it gives for this is the same as that given when i try to boot them using moblin

@afonteijn cheers for the info. i run ubuntu normally so i think this messing with suse should be done in a virtual machine. it will probably take me a few days to test it. cheers tho, and by the sounds of it, it wont be long until it's ported anyway!

Inabit

---

