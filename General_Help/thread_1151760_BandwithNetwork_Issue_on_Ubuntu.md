---
title: "Bandwith/Network Issue on Ubuntu"
date: 2009-05-07
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-07
Hi, I've been having the following issues for some time but didn't care much to report it though it's quite irritating.

1. I use Jaunty on my PC. I also noticed this prob on Intrepid. When I'm downloading something on the same PC or on another one on the network, even when buffering video's sometimes, I can't surf the web with any Internet Browser on my Ubuntu PC. This also happens when I'm updating the system or installing software from the repo's.

2. My network issue is that, I've a built-in Network card on my DELL OptiPlex GXa and seem to have problems with it. I've also got an additional PCI network card installed on this PC which I use to connect to the internet. The PCI one is a VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b) and the built-in one is a 3Com Corporation 3c905 100BaseTX [Boomerang].

Whenever I try to hook up to the network with the built-in card, it connects but internet and network activity is very slow. So irritating was it that I disabled it via the BIOS. I've added two card on this PC coz I had a long term plan for a cluster and also, the VIA adapter happened to be an extra :D. If I recall exactly, my bandwith never reached 40kB/s and hardly hit 30kB/s. Any help on this?

Thanks.

---

### Post by b@sh_n3rd on 2009-05-07
Bump.

---

### Post by wjstarck on 2009-05-07
Please refrain from bumping your posts, especially when you just posted 4 hours ago.

---

### Post by b@sh_n3rd on 2009-05-08
err....now? :D

---

### Post by b@sh_n3rd on 2009-05-10
> **b@sh_n3rd said:**
> Hi, I've been having the following issues for some time but didn't care much to report it though it's quite irritating.

1. I use Jaunty on my PC. I also noticed this prob on Intrepid. When I'm downloading something on the same PC or on another one on the network, even when buffering video's sometimes, I can't surf the web with any Internet Browser on my Ubuntu PC. This also happens when I'm updating the system or installing software from the repo's.

2. My network issue is that, I've a built-in Network card on my DELL OptiPlex GXa and seem to have problems with it. I've also got an additional PCI network card installed on this PC which I use to connect to the internet. The PCI one is a VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b) and the built-in one is a 3Com Corporation 3c905 100BaseTX [Boomerang].

Whenever I try to hook up to the network with the built-in card, it connects but internet and network activity is very slow. So irritating was it that I disabled it via the BIOS. I've added two card on this PC coz I had a long term plan for a cluster and also, the VIA adapter happened to be an extra :D. If I recall exactly, my bandwith never reached 40kB/s and hardly hit 30kB/s. Any help on this?

Thanks.

Anyone?? BTW, I installed Jaunty on another PC with the same card. Thats the one I've mentioned above running Windows. Apparently, this bandwith issue effects Ubuntu PC's. Winblows seems to be able to squeeze through...NVM the bandwith issue let's say, what about the Network card??? :(

---

### Post by nzadLithium on 2009-05-10
Noone can really tell whats going on without more information. Just to hopefully make it simpler for others to read, which may be why your not getting replies (I had difficulty understanding your explanation, it was a bit confusing with so many network cards XP).

Basically my understanding is, you have an ubuntu pc, with an onboard network card (3Com Corporation 3c905 100BaseTX [Boomerang]), and a pci network card (VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)).

And your 3Com card gets slow internet speeds?

I would suggest you do the following:
1) re-enable the 3Com card in your bios (you shouldn't need to disable it, if you want to use the pci network card just plug the cable into the card, you shouldn't need to disable this network adapter for the pci one to work).
2) start up ubuntu with your network cable plugged into the onboard network adapter
3) run lsmod | grep 3c59x
if you dont get a line like:
3c59x  (some number) (another number)
given back to you from that command, then ubuntu has probably loaded the wrong driver, and you will need to remove whatever other driver it loaded, and load that one :D
4) run: sudo ethtool eth0
and sudo ethtool eth1
figure out which of those commands are your onboard network card, and check that the 'supported link modes' you expect to be reported are reported.
Post back what happens :)

Oh and it might have been a better idea to post this in the networking section :p

---

### Post by b@sh_n3rd on 2009-05-10
Well, thanks for your reply. I'll try out your points once I rehook that PC. > (you shouldn't need to disable it, if you want to use the pci network card just plug the cable into the card, you shouldn't need to disable this network adapter for the pci one to work) err...yeah, but you missed a spot...I disabled it not coz I wanted to use the PCI one but coz that stupid card was irritating :D. (not to be rude or anything).> Oh and it might have been a better idea to post this in the networking section :razz:Ahuh, even *I* thought so...only prob is I was soo engrossed in getting an answer, I didn't notice that section and did so, only after I had posted me thread :P.

---

