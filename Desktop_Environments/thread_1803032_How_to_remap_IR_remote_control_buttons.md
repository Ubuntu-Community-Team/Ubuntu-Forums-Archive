---
title: "How to remap IR remote control buttons?"
date: 2011-07-12
forum: Desktop Environments
---

### Post by El Potro on 2011-07-12
Hello community,

I have a pci tv card, which has a built-in IR receiver.

That IR receiver never worked on previous Ubuntu releases. Now, with Ubuntu 10.04, once I select the appropriate module (bttv radio=1 remote=1 pll=1 tuner=38 card=120) to my surprise it worked out of the box. :guitar:

The only issue is that the remote control buttons are incorrectly mapped.

Where is the file that I can edit for changing each button's function? Perhaps it has a GUI that would make the things easier?

This is my output of cat /proc/bus/input/devices

```

# cat /proc/bus/input/devices
I: Bus=0001 Vendor=109e Product=036e Version=0001
N: Name="bttv IR (card=120)"
P: Phys=pci-0000:03:02.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:03:02.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=2c0814 100004 0 0 0 4 2008000 2090 2001 1e0000 4400 0 ffc

```

I'm sure this isn't hard to do, but my ignorance isn't letting me go any further.

Any help will be greatly appreciated.

---

### Post by Apostle_Monkey on 2012-11-15
I am also looking for an answer to this question as I want to re-map some of the keys on my ASRock remote control. I am ideally after mapping a button to a right mouse click so I can use XBMC better on my Raspberry Pi.

I have not had tome to follow it yet but this wiki page looks promising:

[http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255#Determine_the_key_codes_generated_by_your_remote_handset](http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255#Determine_the_key_codes_generated_by_your_remote_handset)

---

### Post by wildmanne39 on 2012-11-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

