---
title: "how to hibernate kubuntu &amp; problem with sound"
date: 2006-01-15
forum: Desktop Environments
---

### Post by solarwind on 2006-01-15
how do you hibernate kubuntu?

i also have a problem with sound

i have two sound devices in my system, one is the built in one and the other is a pci sound blaster card

how do i select which one to use

i want to use the pci sound blaster one

all help is much appreciated

thankyou

---

### Post by solarwind on 2006-01-15
please reply

---

### Post by nrwilk on 2006-01-15
I asked almost the same question.  Maybe some of the responses I got can lead you in the right direction.

[http://ubuntuforums.org/showthread.php?t=88956](http://ubuntuforums.org/showthread.php?t=88956)

---

### Post by Adrian on 2006-01-15
[QUOTE=solarwind]how do you hibernate kubuntu?[/QUOTE]

First of all, you have to enable hibernation. It is done by doing this from a terminal:

```
sudo kwrite /etc/default/acpi-support

```

and uncommenting the "ACPI_HIBERNATE=true" line (by removing the preceeding # character)

If your hardware supports hibernation, you should now be able to hibernate by doing this:
```
sudo /etc/acpi/hibernate.sh
```

If you're using KDM, maybe you can do it from the logout screen too. I'm using GDM at the moment.

---

### Post by solarwind on 2006-01-15
thanks for your reply, but my sound issue is more of a problem.

how do i switch between the active sound device?

(im used to using debian, im new to (k)ubuntu)

---

### Post by nrwilk on 2006-01-15
[QUOTE=Adrian]First of all, you have to enable hibernation. It is done by doing this from a terminal:

```
sudo kwrite /etc/default/acpi-support

```

and uncommenting the "ACPI_HIBERNATE=true" line (by removing the preceeding # character)

If your hardware supports hibernation, you should now be able to hibernate by doing this:
```
sudo /etc/acpi/hibernate.sh
```

If you're using KDM, maybe you can do it from the logout screen too. I'm using GDM at the moment.[/QUOTE]

Ok, I had yet to figure out suspend-to-ram, and I followed your instructions, except I uncommented the line about sleeping instead of the one about suspend-to-disk.  It begins to work, but then it spits this out at the terminal:
```
grep: /proc/acpi/fan/*/state: No such file or directory
```

---

### Post by solarwind on 2006-01-16
thankyou, but my sound problem is more of an annoyance than the hibernation one. How do i switch between my active sound card? I have installed xmms and want to play my music on my soundblaster card, which has much better output quality

---

### Post by solarwind on 2006-01-17
please reply

---

### Post by Adrian on 2006-01-18
[QUOTE=Fealos]Ok, I had yet to figure out suspend-to-ram, and I followed your instructions, except I uncommented the line about sleeping instead of the one about suspend-to-disk.  It begins to work, but then it spits this out at the terminal:
```
grep: /proc/acpi/fan/*/state: No such file or directory
```[/QUOTE]

That happens to me too. I haven't managed make suspend-to-ram work on linux yet, even though my hardware supports it. Seems like the function doesn't work on a great number of computers *yet* (hence being disabled by default in all distros I've tried).

When I used Freebsd, I could suspend my machine, but that was using APM and not ACPI. Since I prefer hibernation anyway, I haven't done any experimenting since I got that to work.

---

### Post by Adrian on 2006-01-18
[QUOTE=solarwind]please reply[/QUOTE]

I'm sorry, I don't have any solution since I've never tried using two sound cards in a Linux machine. All I can do is to suggest the obvious: why not disable the onboard sound from the BIOS? 

Shouldn't be necessary though.

---

