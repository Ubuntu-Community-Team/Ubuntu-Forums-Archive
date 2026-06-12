---
title: "Problems with booting up and shutting down."
date: 2009-03-28
forum: General Help
---

### Post by studysession on 2009-03-28
Hey everyone. I am a new ubuntu user. Last week I installed ubuntu 8.10 on my laptop and I am having some minor problems with booting up and shutting down ubuntu. I have been searching through these forums and have not been able to come to a solution myself. 

When I turn on my computer I get the grub menu and select ubuntu. Then when the splash screen shows up with the orange rectangle that bounces back and fourth everything will stop. I have to hold down any key on my keyboard to make the bar move until I get to the part where that bar stops bouncing back and fourth and begins to load. 

Also when I shut down ubuntu the splash screen has alot of graphical problems. There are alot of green lines that appear and disapper across the screen as well and blue dots. The ubuntu logo also moves around a little bit. This is not a major problem but it is a little annoying.

I have heard good things about ubuntu and its support community so I hope some of you will be able to help me out.

Thanks

---

### Post by cariboo on 2009-03-28
This is a very common problem, with many laptops, especially HP/Compaq. Add the following to the kernel line in grub:

```
hpet=disable
```

To edit grub, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

The above command will open gedit as root allowing you to edit the file:

the line you are looking for looks something like this:

```
kernel          /boot/vmlinuz-2.6.27-11-server root=UUID=1b3daa9a-d347-4853-9565-f9979abb8e90 ro quiet splash 

```

You have to add the above command to the end of this line.

Note: the line above is for my server, as I am on a computer running AntiX, and the kernel lines in thei distro are completely different from Ubuntu, The kernel line should specify a generic kernel.

Jim

---

