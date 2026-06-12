---
title: "Display resolution through a KVM"
date: 2009-06-10
forum: Desktop Environments
---

### Post by skicrazer on 2009-06-10
I've posted this in the Linux Mint and PC World forums and they gave pretty good responses, but not a final answer.  It was also suggested that I try here, given that Mint is mostly Ubuntu at the core.

With my new Mint 6 XFCE Felicia CE /n /l installation (used XFCE due to low system resources), I can only get 800x600 resolution when connected to my KVM switch, yet my monitor can go to 1024x768. When I bypass the KVM and connect the monitor directly to the Mint PC, it displays at the full 1024x768. Yes, you say, it is, therefore, the KVM switch that is limiting my resolution! But, my question is, how is it that my Win XP PC, connected to another port on the KVM is displaying 1024x768? Is it something that XP does that Linux doesn't (I'd assume not!). 

Upon the Mint forum's suggestion, I ran 'xrandr' with the following results:

Screen 0: minimum 400 x 300, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
800x600 60.0* 56.0 
640x480 60.0 
400x300 60.0 56.0

So, like any good detective, I tried switching the ports, so Mint ran off the port Win was on before and vice versa. Result? Yep - Mint at 800x600, while Win came up at 1024x768 again.

I also ran the lspci | grep VGA command, which returned:

01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)

Don't know if that would help solve this mystery (?). Could it be that the KVM understands one video controller, but not another?

Thanks for any help you can provide.

---

