---
title: "installation on laptop not possible"
date: 2005-06-08
forum: Desktop Environments
---

### Post by Hägar on 2005-06-08
Good morning at first and hello, I´m new in this community.
I have a problem with installing kubuntu on my laptop, a IPC Highnote S15.
When I start the installation with "expert acpi=off" it says "loading /install/vmlinuz" then "loading /install/initrd.gz" and then "Ready" with a very long beep (about 3 or 4 seconds) and that´s it. No more booting and it doesn´t take any keyboard command.
I tried with "expert", "linux", "linux acpi=off" and it´s every time the same except the beep. The beep only comes in expert mode :???: 
Anyone who has an idea what can be the problem?
By the way, I already installed another pc with this cd and I have running Suse 9.0 on this laptop.

Have a nice day,

Gerd

---

### Post by johnprgr on 2005-06-08
I don't know if this will help, but I know every laptop I've ever purchased needed "nolapic" as a boot parameter to work right.  Also you may need acpi=on laptops are pretty picky about acpi these days.

I wish I had more advice for you, but I hope this helps or maybe gets you going in the right direction.

---

### Post by kvidell on 2005-06-08
[QUOTE=johnprgr]I don't know if this will help, but I know every laptop I've ever purchased needed "nolapic" as a boot parameter to work right.  Also you may need acpi=on laptops are pretty picky about acpi these days.

I wish I had more advice for you, but I hope this helps or maybe gets you going in the right direction.[/QUOTE]
 That's weird. I've installed on 3 laptops now (granted; all ibm's) and never needed to do anything other than hit my [enter] key at the "boot: " prompt after the cd boots in.

However I have added those things to my kernel line in /boot/grub/menu.lst to get suspend via apm working.

to Hager:
Have you tried not passing it ~any~ arguments?

---

### Post by Hägar on 2005-06-08
I tried it without any parameter and with nolapic and with acpi=on and it´s all the same

---

### Post by nocturn on 2005-06-08
[QUOTE=Hägar]I tried it without any parameter and with nolapic and with acpi=on and it´s all the same[/QUOTE]

Some more options:
pci=noapci noapic

Good luck

---

### Post by Hägar on 2005-06-08
the same procedure as every time with noapic

---

### Post by dejitarob on 2005-06-08
Have you tried booting off the LiveCD? If it works you would at least know its possible.

---

### Post by Hägar on 2005-06-08
it´s the same thing with the live cd

---

### Post by dejitarob on 2005-06-08
I couldn't find any info on setting up Linux on your laptop but I did find [something](http://gerda.univie.ac.at/freebsd-laptops/index.pl?action=show_laptop_detail&laptop=274) for freebsd. Peculiarly, it says APCI is only partially-working..

---

### Post by dejitarob on 2005-06-08
Have you tried looking [here](http://www.ubuntu-forum.de)?

---

### Post by az on 2005-06-08
[QUOTE=Hägar]Good morning at first and hello, I´m new in this community.
I have a problem with installing kubuntu on my laptop, a IPC Highnote S15.
When I start the installation with "expert acpi=off" it says "loading /install/vmlinuz" then "loading /install/initrd.gz" and then "Ready" with a very long beep (about 3 or 4 seconds) and that´s it. No more booting and it doesn´t take any keyboard command.
I tried with "expert", "linux", "linux acpi=off" and it´s every time the same except the beep. The beep only comes in expert mode :???: 
Anyone who has an idea what can be the problem?
By the way, I already installed another pc with this cd and I have running Suse 9.0 on this laptop.

Have a nice day,

Gerd[/QUOTE]


Please file a bug report.

bugzilla.ubuntu.com

---

### Post by Hägar on 2005-06-09
I know that there are sometimes problems with ACPI but I already tried to turn it off on install. By the way, I remember that I also tired to install Suse 9.2 on this laptop and I had the same problem. But the Suse support told me, that the installer needs at least 128MB RAM and that my graphic card takes some of my 128MB Ram so that I´m below the minimum for suse 9.2 But Ubuntu doesn´t need 128MB, right?

---

### Post by Hägar on 2005-06-09
[QUOTE=azz]Please file a bug report.

bugzilla.ubuntu.com[/QUOTE]

But what should I write in a bug report. There is nothing what I can tell so that someone can test this. I think it´s a special problem with my laptop and not really a bug.

---

