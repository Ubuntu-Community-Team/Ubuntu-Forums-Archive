---
title: "inspiron 1525 fails to hibernate on karmic"
date: 2009-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nastareger on 2009-11-10
I recently upgraded my Ubuntu installation to Karmic (running dual boot with WinVista, btw) and all seems to work fine, except for hibernating. When I tell my laptop to go to sleep, it'll fade the screen to black as usual, but afterwards, nothing happens. When moving/clicking the mouse or pressing a key, the input-password dialog appears, just as if I locked the computer. Authenticating again and getting back to where I was then works, but at this point, regular shutdown is not an option anymore, it'll just stall when I ask it to do this. Only way out is an 8-second-button press, which doesn't seem very healthy to me.

Moreover, I like hibernate. It used to work perfectly, so I can't think of a reason why it wouldn't work now. I had a look at the bug reports and there were some similar cases reported, but none of them seemed to contain the same symptoms. Anyone got some advice? Thanks!

---

### Post by jnorthr on 2009-11-10
perhaps this might be due to a change in the APIC power control logic which was revised in 9.10 (i've read) so it might not provide identical results to 9.04 usage. Can you use the suspend feature to achieve what you want to do ?

---

### Post by Nastareger on 2009-11-13
Thanks... good to know. Suspend is actually not sufficient, as it still consumes some power when it is in that mode... and I use hibernate to shut the laptop down for a few days off AC power while still being able to save my session.

Furthermore, I noticed that it seems to work sometimes... I think I determined some factors that seem to have an influence. Among them is turning off the wireless unit manually (button on the side) before trying to hibernate, it looks like the software has trouble doing this by itself. Another one is completely leaving it at rest after pressing 'hibernate'... this involves not even moving your mouse. Strange, but the times I tried, it actually did go into hibernate... I'll keep this updated when I find out more!

---

### Post by debsankha on 2009-11-14
This may be due to inadequate swap space in your hard disk. Since ubuntu writes all the data on the RAM to the swap partition on hibernating , you should have a swap no smaller than the total RAM  in your system in order to make hibernation work properly.

---

### Post by Nastareger on 2009-11-21
I found out my swap is set to 5.9 GiB - so at least as large as my RAM, considering I'm running 32-bit. I'm still guessing it's a hardware problem.

More and more often I notice that this seems to be one of the few things 'wrong' with Ubuntu... support for proprietary hardware is inadequate or lacking in a little too many cases. Oh well, I'll just live through this and we'll see how it turns out. Getting an 'Ubuntu-ready' laptop next time doesn't seem like a bad idea.

Still, thanks for the help!

---

### Post by rogerggbr on 2009-11-26
Just to let you know - same here, you are not alone. Randomly works, but mostly doesn't. I have resorted to proper shutdowns for the moment.

---

### Post by speedkx on 2009-12-08
Same here with a Sony laptop. Suspend still works after upgrade, hibernate - not anymore. I've also manually installed kernel 2.6.32 with no results. Hibernate used to work perfectly since at least 8.04, now it doesn't.

---

