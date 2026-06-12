---
title: "Mouse Scroll lost after switching on KVM"
date: 2006-11-03
forum: Desktop Environments
---

### Post by mindseye1 on 2006-11-03
I just upgraded my Dapper installation to Edgy and came across an issue with my mouse. I have a Logitech MX510 and a KVM that switches between Ubuntu, XP, and another Debian/KDE Desktop. When I boot up Ubuntu, my scroll wheel works fine. As soon as I switch to XP or Debian and then back to Ubuntu, I have lost the scroll functionality. Also, the scroll continues to work fine in both the XP and Debian installs, so I know it is not a hardware issue. In addition I never had this problem with Dapper so I am not sure what changed.

I have seen a few posts about this, but they all just provided temporary annoying fixes like unplugging the mouse or running a script to fix the mouse each time you switch. These are unacceptable for an OS that is trying to become mainstream. Can anyone provide me ideas for a permanent fix for this issue? I can't imagine that it is very difficult since it worked in Dapper and my other Debian system. Thanks for any help you can provide!

-mindseye1

---

### Post by gumbald on 2006-11-04
Have you set a custom configuration for the mouse or is it the default settings?

---

### Post by mindseye1 on 2006-11-04
I've tried both. This is my current config:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by dove on 2006-11-04
/

---

### Post by Peepsalot on 2006-11-04
> **mindseye1 said:**
> I just upgraded my Dapper installation to Edgy and came across an issue with my mouse. I have a Logitech MX510 and a KVM that switches between Ubuntu, XP, and another Debian/KDE Desktop. When I boot up Ubuntu, my scroll wheel works fine. As soon as I switch to XP or Debian and then back to Ubuntu, I have lost the scroll functionality. Also, the scroll continues to work fine in both the XP and Debian installs, so I know it is not a hardware issue. In addition I never had this problem with Dapper so I am not sure what changed.

I have seen a few posts about this, but they all just provided temporary annoying fixes like unplugging the mouse or running a script to fix the mouse each time you switch. These are unacceptable for an OS that is trying to become mainstream. Can anyone provide me ideas for a permanent fix for this issue? I can't imagine that it is very difficult since it worked in Dapper and my other Debian system. Thanks for any help you can provide!

-mindseye1
I had this same problem before.  But, unlike you, the problem was present in Dapper as well.  Unfortunately the only real solution that worked for me was to get different, more compatible KVM (IOgear gcs62) instead of the no-name one I was using.  Are you using a different KVM than when you had Dapper?
What KVM are you using?

This is the thread that helped me:
[http://www.ubuntuforums.org/showthread.php?t=187018&page=2&highlight=kvm](http://www.ubuntuforums.org/showthread.php?t=187018&page=2&highlight=kvm)

---

### Post by mindseye1 on 2006-11-04
The KVM is a TrendNET TK-400. It is a 4-way, but it is the same one I had in Dapper. I know that the hardware is fine though, because like I was saying, one of the OSes I switch between is Debian with a KDE Desktop. Since it works fine there, I would assume that Ubuntu can get it to work fine as well. There has just got to be some type of hidden configurations or driver options that I'm not seeing.

As for the horizontal scrolling, you may want to check your Z-axis mapping in your xorg.conf. Perhaps it is not set to "4 5" like the configuration I posted above.

---

### Post by Peepsalot on 2006-11-04
Well, I think I read somewhere that this is some sort of kernel issue, so it may be an issue of finding a kernel version that works and sticking to that.  Sorry I don't know any more than that.  Good luck.

---

### Post by mindseye1 on 2006-11-05
Could anyone advise me as to which files I could compare between my Ubuntu and Debian systems that might point me in the right direction of finding the problem? I've already check through my entire xorg.conf and the problem does not lie there. Any ideas?

---

### Post by adderman on 2006-11-06
Hi, the problem is almost certainly the KVM switch. The perception is that a KVM switch is a KVM switch, this is an example that shows this not to be true. Many KVM switches are cheap and cheerful and one way to keep costs down is to minimise the keyboard and mouse emulation (and other things such as DDC emulation, USB keep alive and Sun country code reporting). Like most things in life you pay for what you get.

A proper KVM switch should solve this problem, see [http://www.adder.com/main.asp?id=508_2040_22698&mode=Specification](http://www.adder.com/main.asp?id=508_2040_22698&mode=Specification) 

Yes it will be more expensive and yes I work for them but as I say, you get what you pay for, you would not expect to be able to buy the cheapest video card and the cheapest monitor and be blown away by the picture.

---

### Post by mindseye1 on 2006-11-06
> **adderman said:**
> Hi, the problem is almost certainly the KVM switch. The perception is that a KVM switch is a KVM switch, this is an example that shows this not to be true. Many KVM switches are cheap and cheerful and one way to keep costs down is to minimise the keyboard and mouse emulation (and other things such as DDC emulation, USB keep alive and Sun country code reporting). Like most things in life you pay for what you get.

A proper KVM switch should solve this problem, see [http://www.adder.com/main.asp?id=508_2040_22698&mode=Specification](http://www.adder.com/main.asp?id=508_2040_22698&mode=Specification) 

Yes it will be more expensive and yes I work for them but as I say, you get what you pay for, you would not expect to be able to buy the cheapest video card and the cheapest monitor and be blown away by the picture.

I'm sorry, perhaps you didn't read the entire thread, but the KVM switch is fine. This is proven by the fact that it works in Windows XP, Debian with KDE, and Ubuntu's Dapper Drake release (and I'm sure I could add more OSes to this list if I actually believed it was a hardware issue and wanted to test more). The problem most certainly lies in either a driver or some configuration file that was changed during the upgrade, or perhaps even differences in the kernel. So again, if someone could help me identify any files I could do comparisons on that would be great. Thanks again for the help!

---

### Post by pony-tail on 2006-11-07
I have (am still ) had this issue with both Dapper an edgy on 2 different KVMs - both work fine on other distos - (one is an Aten Master-View the other is a D-Link ) but both lose the mouse (it just goes screwy )on switching to the other unit and switching back - the keyboard is fine . The issue is definately the mouse emulation on the hub . The problem is the method of implementation some are much better than others - and just because it is an expensive unit does not necesarily mean it will be better - I have a very old Ho-Sin made in Se Asia somewhere (the writing is in an asian language ) PS2 KVM that works fine - even on dapper but the Video quality sucks past 1024x768 no keyboard and mouse issues though it has a separate power brick though and it is bulky 8"x5"x2" for a 2way - point is it is a cheap and nasty but works the other 2 are mid price and do not .I will be trying a Belkin "soho" as soon as it arrives (it has Audio and PS2 as well as usb ) hopefully it will work better makes for expensive experimentation . All of these work fine with Fedora so go figure.
I have six computers all very different but use only 3 monitors hence the need for KVMs .
Ask around till you find someone who has had success with one on Ubuntu then buy the same Make and model - Maybe a usb one would work better because PS2 mice on KVMs in Linux can be touch and go .

---

