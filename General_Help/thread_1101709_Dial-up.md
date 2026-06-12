---
title: "Dial-up"
date: 2009-03-20
forum: General Help
---

### Post by jfalco on 2009-03-20
So here's my deal:

I'm going to install intrepid on my mom's pc and she lives in the middle of nowhere. She doesn't have internet access. Is there anyway I can dial into her system through our 56k modems and fix stuff when she messes up? Also would it be possible to install updates this way (I know it would be slow) and could she access the net through my connection?? Thanks for the help!!

---

### Post by linuxisevolution on 2009-03-20
> **jfalco said:**
> So here's my deal:

I'm going to install intrepid on my mom's pc and she lives in the middle of nowhere. She doesn't have internet access. Is there anyway I can dial into her system through our 56k modems and fix stuff when she messes up? Also would it be possible to install updates this way (I know it would be slow) and could she access the net through my connection?? Thanks for the help!!

What do you mean through your connection? Yes, but it would be pointless since her modem is only 56K. Even if your connection was 1Tb, her experience would still be 56K. Everything should work fine, it will just be slower for net access. Yes you can access her pc using ssh or vncviewer. vncviewer is refered to as Remote Desktop in Ubuntu.

On her system, click System >> perfrences >> remote desktop. and enable it, with a password. Then on your system, click Applications >> Internet >> remote desktop and enter the ip address or whatever info dial up has.

---

### Post by lisati on 2009-03-20
One possibility (if you have a good connection speed) would be to do the basic setup of your mum's machine at your place, and install all the updates, and then, as suggested, use the remote desktop if your mum calls for help.

---

### Post by jfalco on 2009-03-20
Thanks for the replies guys! I'm familiar with ssh and what not but I want to be able to dial her phone number from my pc and have her pc answer and then be able to control it. I have no idea how to do this??? Any help??

---

### Post by linuxisevolution on 2009-03-20
> **jfalco said:**
> Thanks for the replies guys! I'm familiar with ssh and what not but I want to be able to dial her phone number from my pc and have her pc answer and then be able to control it. I have no idea how to do this??? Any help??

If her pc isn't dial on the internet on the first place you cannot connect it, she has to, and as I explained in my above post take control of it with remote desktop.

---

### Post by lisati on 2009-03-20
> **jfalco said:**
> Thanks for the replies guys! I'm familiar with ssh and what not but I want to be able to dial her phone number from my pc and have her pc answer and then be able to control it. I have no idea how to do this??? Any help??

I'll have to pass on the remote dial-in thing: my awkwardly small networking experience is limited to multiple computers hooked up to the one router.

---

