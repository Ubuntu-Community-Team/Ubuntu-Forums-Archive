---
title: "Superfast boot?"
date: 2009-03-28
forum: General Help
---

### Post by azhtar on 2009-03-28
Hi everyone, I've been wondering, how can i get ubuntu to boot as fast as the aspire one linux distro but on my PC?

You know, the aspire one is pretty damn weak compared to a lot of desktops.

Is there a **how to** for noobs like me :lolflag: to get the kernel optimized for my hardware?

Also there's another stupid questin I want to ask.

Is there a way that I can start Windows directly without having to restart the machine? I'm a gamer, so, sometimes I hate when I'm on linux and my friends invite me to join them to kick some asses on Call of Duty 4 and it takes some precious time to watch the computer starting all over again just to select windows on the loader screen, also i try to keep as open source as posible, but I don't know how to survive without Photoshop CS4 (GIMP is good, but not that good).

It would be awesome to do that.

---

### Post by halavin on 2009-03-28
if you are just trying out linux then you can install vmware and boot linux off of it . You can run both windows and linux at the same time (  you can switch between the OSes). 

or install vmware or virtual box on linux and use Windows OS as a guest OS.

This way you dont have to reboot. Since your games seem to run on windows , I  would install vmware on windows and invoke the linux as a guest OS

As far as super fat boot goes, you can totally strip down all you linux services to a bare hardware box with only the apps you want to run. This needs customization. Also try busybox it that helps your cause


hope this helps

---

### Post by azhtar on 2009-03-28
Thanks, but I don't want to use virtual machines, they all suck, have you tried playing crysis on any virtual machine? :lolflag: it sucks, also in the other way, using any VM makes any Linux run as $%&)

Also, well, maybe I'm not that noob, I've using ubuntu since 7.04 as my preferred OS, but I sincerely don't understand everything as I would want to, my trend is just to copy codes and paste them on the console while researching a little bit before I mess with the system.

---

### Post by 3Miro on 2009-03-28
> **azhtar said:**
> 
Also, well, maybe I'm not that noob, I've using ubuntu since 7.04 as my preferred OS, but I sincerely don't understand everything as I would want to, my trend is just to copy codes and paste them on the console while researching a little bit before I mess with the system.

Good policy in general, measure twice cut once.

For games, you can try wine. I was able to get all of my games running on wine (you probably want to add the winehq repository since it is better). Setting a game can be tricky and I suggest reading on the winehq forums (also looks at the dates and the wine version for the different posts, wine today is totally different from wine 2 years ago). Once a game runs under Linux, it runs and you should be able to do LAN with your friends from within Linux (now that would be cool).

---

### Post by azhtar on 2009-03-30
I don't think using wine I could achieve the same frame rates as in Windows, also, don't get me wrong, while I prefer Ubuntu for some stuff it doesn't mean everything, I do like Microsoft software, I also buy Windows because there are programs meant to be run ON Windows, in this case Games and Photoshop.

And what about the restart topic? is there some way I can achieve this?

---

### Post by hockeyhead019 on 2009-03-30
I've been looking for an answer to this also as i hate restarting my machine for windows just to play online for a little... but i wouldn't recommend wine as you're right... to much hassle not enough reward for me personally haha

---

### Post by Locutus_of_Borg on 2009-03-30
fast booting: einit
booting windows : don't

there's no way to start windows within linux apart from a VM
you have to reboot


einit will give you really fast boot times (3-5 seconds after kernel initializes until X starts)

---

### Post by hockeyhead019 on 2009-03-30
what specifically does einit do that speeds up the process?

---

