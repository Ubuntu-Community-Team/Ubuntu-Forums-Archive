---
title: "Hotplug freezes on first boot"
date: 2006-01-13
forum: General Help
---

### Post by nick_jensen on 2006-01-13
I am trying to install Ubuntu to a [Sager NP-5320V]("http://www.sagernotebook.com/pages/notebooks/product2.cfm?ProductType=5320&SubType=V") laptop. The install seems to go fine, but then on the first boot, at "Hotplug Subsystem Starting" the system seems to freeze. Trying to boot with kernel options nohotplug and/or noapic nolapic doesn't seem to have much effect. Just wondering if anyone has any other ideas that I can try?

---

### Post by sebweb on 2006-01-13
re install ubuntu

---

### Post by nick_jensen on 2006-01-15
[QUOTE=sebweb]re install ubuntu[/QUOTE]

I've reinstalled several times, each with different options, and each with the same result.

---

### Post by LargoSensei on 2006-04-26
I alsop have a sager Laptop NP3880-V. and I also suffer from the "hotplug Subsystem freeze" anyone have any ideas whatsoever?

---

### Post by ctothej on 2006-04-29
I also have this problem, though I am on a desktop. Why is it not intuitive enough to time out when searching for devices? Maybe someone can elaborate on exactly what the hotplug subsystem does and in what steps.

---

### Post by Bone Down on 2006-05-05
i am also having this same problem as well.

np3880-c  I have re-installed now 12 times and no change at all.

I am a bit of a newb to linux on the laptop and this will be my third install on a laptop and this is the first one that I have ad issues with.

---

### Post by Bone Down on 2006-05-05
bump for the friday night crew

---

### Post by physcsdrk on 2006-05-06
I have this issue sometimes as well.  I had to reinstall earlier today because of another issue so I don't know if i will have it again but here is my two cents worth anyway.  I am super new to linux so I am not sure what hot plug is but I figured it had to do with usb so i just started unplugging things and rebooting until it worked.  It also only happened on some boots.  So if it happened I would unplug and reboot.

---

### Post by Bone Down on 2006-05-06
[QUOTE=physcsdrk]I have this issue sometimes as well.  I had to reinstall earlier today because of another issue so I don't know if i will have it again but here is my two cents worth anyway.  I am super new to linux so I am not sure what hot plug is but I figured it had to do with usb so i just started unplugging things and rebooting until it worked.  It also only happened on some boots.  So if it happened I would unplug and reboot.[/QUOTE]

unfortunately I have not even been able to get past the intial install reboot and this is a fresh install on a brand new laptop, nothing plugged into the USB ports.

Half of the installs were with the PC not plugged into the network and the other half it was plugged into the network and it produces the same effect either way.

looking for more suggesitons.

---

### Post by rdtran1 on 2006-05-11
I have this same problem on my asus z63a....

---

### Post by nos4a2 on 2006-05-13
Me too - Evesham C720 laptop. I've tried with and without XP Pro as a second OS. I've tried a complete disk wipe using DBAN before install. There is nothing plugged into the laptop. It always hangs at "Hotplug Subsystem Starting". Initially it stops at the Ubuntu splash screen (the one with the logo and the progress bar) but after a couple of minutes it drops to a comand line type screen - but still hung at the same point.

---

### Post by arthus on 2006-05-13
I have the same problem on my new desktop build. The motherboard is an Abit AT8 32X. I have tried unplugging all connections (USB, Firewire, PS2). This is my first Linux install so I am very confused. Also, there it won't detect my ethernet adapter but that requires special drivers whcih my motherboard says I will need to install later; even for Linux. 

-The Confused Newb

---

### Post by Tamale on 2006-05-17
Same problem here on an older supermicro 1U server.. dual Pentium III 1ghz processors...

anyone???!?

---

### Post by DOtSlaSHuCantCME on 2006-05-18
Im on an Hp system and what was causing my hotplug problem was my BIOS listing my Onboard
video as "PCI" instead of "Onboard",boot to Bios  and change your onboard listing to Onbard,if indeed your video is onboard your motherboard and not a Pci device(card).

---

