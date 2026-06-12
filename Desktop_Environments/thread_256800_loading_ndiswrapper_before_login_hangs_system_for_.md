---
title: "loading ndiswrapper before login hangs system for 5 minutes"
date: 2006-09-13
forum: Desktop Environments
---

### Post by NoTiG on 2006-09-13
Hello

I have a weird problem. Im using the broadcom wifi card. My wifi works... but only if i  sudo modprobe ndiswrapper after i finish loading. 

If i write the configuration to modprobe.d  by typing:

ndiswrapper -m

Then when i boot up it will hang after i enter my name and password... for about 5 minutes before it loads. Is there some file i need to edit somewhere with a timeout or something ? 

Ps. how do you file bugs in ubuntu ? is there an application hidden somewhere?

---

