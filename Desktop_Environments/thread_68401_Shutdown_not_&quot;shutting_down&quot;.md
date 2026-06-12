---
title: "Shutdown not &quot;shutting down&quot;"
date: 2005-09-23
forum: Desktop Environments
---

### Post by nkessler2000 on 2005-09-23
After having a generally good experience with Ubuntu on my desktop, I decided to put  Ubuntu on my old IBM Thinkpad T20. It works great except for one rather significant problem: Doing a Shutdown does not power down the computer. It gets to a screen that says "Power Down", you hear the hard disk stop, and then it just sits there. You have to hold the power button down for a few seconds to get it to turn off. It doesn't matter how I shut down either: Shutdown from the Logoff menu in Gnome, shutdown -h now from a command prompt, either way I get the same result. Any suggestions on how to fix that? 

Oh yeah one more very minor problem with running Ubuntu on the Thinkpad. The step during boot where it syncs the time to Ubuntu's time server fails if I'm using wireless networking. I guess it's because the wireless card gets initilized after that step. Anything I can do about it? If not, it's not a major thing.

---

### Post by Vulc on 2005-09-28
its been a long time since I've seen a comp do that, but from what I remember, there should be an option in your bios to enable something like "advanced power management" or something along those lines. If that is disabled it hangs waiting for you to cut the power. If that's not the reason why its hanging....no idea =)

---

### Post by joshuapurcell on 2005-09-28
I've had the same exact problem on my T21 since installing Hoary. I've think that adding this to the kernel line of your /boot/grub/menu.lst file may help:```
acpi=off
```
I think I tried this and it worked, but it's been a while since I've checked. I'll get back to you on this when I'm able to check my config.

EDIT: Doesn't look like acpi=off works... but I know that at one time I added an argument to the kernel line that allowed me to reboot or shutdown my Thinkpad without running into weird problems (or forcing a hard powerdown). My laptop always shutsdown, but sometimes it will shutdown gdm nicely and show the command prompt while doing so (it never shows all the processes shutting down), and sometimes it goes to a weird coloful screen made of horizontal green and pink lines (which is more common). I'll figure out what I did to fix it and try it again.

---

### Post by Nasso on 2005-10-08
i got the same problem. If anyone got the solution, please update :)

---

