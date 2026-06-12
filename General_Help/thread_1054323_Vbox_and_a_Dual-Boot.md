---
title: "Vbox and a Dual-Boot"
date: 2009-01-29
forum: General Help
---

### Post by Matsuri on 2009-01-29
Here is the scoop, I have a dual booted machine with Ubuntu and XP. I use the XP install to game. I would like to not have to boot into XP ever and the games are a little hardcore for WINE. Is there a way I can use vbox to startup and run the XP install while in Ubuntu?

Thanks,
Matsuri

---

### Post by khedron on 2009-01-29
Just to warn you that virtual machine environments can't do graphics properly, so you won't be able to play games on vbox+XP either. That's unless vbox is unlike all other virtual machine environments that I've seen.

---

### Post by khedron on 2009-01-29
The problem that Virtual Machines and WINE have is that there is no direct mapping between Windows (DirectX) graphics operations and Linux (OpenGL) graphics operations. So they have to use the CPU for just about all graphics, which is very slow.

---

### Post by Matsuri on 2009-01-29
anyway to boot and run windows from inside linux to get me around this problem? I'm also just thinking about when MS stops supporting XP. I'm not using Vista or Win 7 on the account that both are trash. However, I still want to be able to play the few games I enjoy. Any way I can start running slightly more hardcore windows games in unix?

---

### Post by khedron on 2009-01-29
To be honest, not that I can see due to this graphics problem. There's no way of letting Windows access the graphics card directly while running in Linux either.

I think the only solution here is to keep dual-booting.

You could try minimising the size of your XP install and then trimming down the partition, if you're worried about space. For example, I have a small (5G) Win2000 partition on my server that I keep around for when friends come over and I can network Starcraft. Win2000 is unsupported by MS, but that shouldn't matter since I'm behind a router that blocks all incoming requests and I only use it for games, not browsing. Thus it won't be affected by security vulnerabilities.

---

### Post by Matsuri on 2009-01-29
My windows partition doesn't take up much of the harddrive. I hate rebooting just to play a game. Then having to reboot again to do work and keep up to date with everything else. Hence the question.

---

### Post by Universal344 on 2009-01-29
Two things:

1. I think XP can access your graphics if you install guest additions.  under the machine menu I believe when your machine is running click "install guest additions."  You should wait for someone to confirm this because I could be wrong.

2. If you try this there is an option under settings that says "enable 3D acceleration."  Don't use it.  It only works with Linux guest installs because it only accepts openGL not directX.  

Hope this helps.

---

