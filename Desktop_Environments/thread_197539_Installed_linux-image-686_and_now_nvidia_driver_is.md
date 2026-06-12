---
title: "Installed linux-image-686 and now nvidia driver is hosed"
date: 2006-06-15
forum: Desktop Environments
---

### Post by mark2741 on 2006-06-15
As a newbie you'd think I'd not mess with things so blindly.... : ) 

Based on a previous thread about using the 686 kernel instead of the 386 kernel I thought I'd give it a go since I'm using a P4 1.7ghz processor. I installed and synaptic told me I needed to reboot. Once I rebooted, X wouldn't start and I got an error saying the nvidia driver (or card, I forget) is hosed. 

Fortunately the 386 kernel is still installed so I was able to reboot into that. So how do I fix my ubuntu to work with the 686 kernel? I'm using an Nvidia legacy card: Ti4200. That said, I used Automatix to install the nvidia driver and by default it installed the glx/non-legacy driver and everything's been fine so I've left it.

---

### Post by glotz on 2006-06-15
That Ti4 is not considered legacy yet. You'll need the matching module to go with the kernel, see 
> Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)


(Dump automatix, imho)

---

### Post by kpkeerthi on 2006-06-15
Yep. You have to re-install the binary nvidia driver and you are good to go.

After upgrading to 686 kernel on my lappy, my **idle** cpu usage constantly peaked 35-50%. See [http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833) for a fix if it happens to you too.

---

### Post by mark2741 on 2006-06-15
Thanks guys. I installed the restricted modules and it works now! I'm running the 686 kernel. I'm noticing some slight constant activity in the system monitor that I don't recall noticing when running the 386 version, but it's less than 5 or 10% tops so I guess everything's okay.

I only have 512mb of RAM and I think I need more. How much ram do you guys use?

---

### Post by kpkeerthi on 2006-06-15
2 gb :D I use my lappy primarily as a gaming station. I'm dual booting with win XP. I've installed dapper for grins and giggles.

---

### Post by glotz on 2006-06-15
0.192 gigs.

---

### Post by Gustav on 2006-06-16
install the meta-package linux-686 to get the right restricted modules package automaticly (how do you spell that word? :-/).

---

### Post by glotz on 2006-06-16
automatically :) like your sig and avatar!

---

### Post by Gustav on 2006-06-16
[QUOTE=glotz]automatically :) like your sig and avatar![/QUOTE]
Thank you and thank you!

---

