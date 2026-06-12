---
title: "Need to manually start X when booting"
date: 2010-06-21
forum: Desktop Environments
---

### Post by SteelSlasher on 2010-06-21
When I first installed Lynx it would boot fine but as the first kernel updates came in it began to get really dodgy. Some days a certain kernel would boot up fine whereas the other would boot without X (i have dual boot with XP and so the kernel options come up on GRUB)

Just today I updated the NVIDIA drivers  and now neither boots fine, I looked around and I found that after logging in running "startx" in the CLI, which is displayed instead, i get my normal desktop back again.

Should I just try and set up my ubuntu to run startx automatically or is there something else i should do?

---

### Post by dabl on 2010-06-21
Next time you boot the computer, try 

```
sudo service gdm stop
```

```
sudo service gdm start
```

It should either provide the Gnome login greeter, or else give you error output that will help troubleshoot.

---

### Post by SteelSlasher on 2010-06-22
the problem seems to have subsided

---

