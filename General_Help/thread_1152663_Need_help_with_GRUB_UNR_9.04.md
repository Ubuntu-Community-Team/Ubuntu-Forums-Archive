---
title: "Need help with GRUB: UNR 9.04"
date: 2009-05-08
forum: General Help
---

### Post by bg8780 on 2009-05-08
Hey guys, I just installed UNR on my U100-432US. I am surprised that wireless works fine since I have the Ralink N card and not the more common realtek one but anyway I am having a number of issues. Let me start off by saying this is a dual boot with Ubuntu Netbook Remix and Vista Business

I am only able to select which OS I want to boot when the vista disk is in my external optical drive. If the drive is not connected GRUB boots directly to Ubuntu skipping over the menu to choose which OS to boot completely. I looked in grub (when I hit "e" on the vista bootloader) Vista's bootloader has these following properties. 

rootnoverify (hd0, 1)
savedefault
chainloader +1

I am able to change these values and add new ones however they are not saved.

This OS seems very cool and runs fine when I have the optical drive connected but when booting from nothing being connected it skips over selecting and OS and just boots Ubuntu and also the touchpad doesnt work.

Thanks for the help guys I really appreciate it, however keep in mind I am a COMPLETE noob with Linux distro's so when describing to change options and parameters in GRUB please post it very clearly and assume I have no knowledge of GRUB or how it operates (because I pretty much don't). Essentially make it idiot proof. lol

Thanks again guys! I really appreciate the help and I cant wait to be using a fully functional UNR install, this OS seems very useful and fun!

---

