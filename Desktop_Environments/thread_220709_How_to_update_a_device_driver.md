---
title: "How to update a device driver"
date: 2006-07-21
forum: Desktop Environments
---

### Post by saul_2110 on 2006-07-21
I've got a problem with my wireless card [an atheros 5005G]; when the wlan is not available or I disable the card, it starts making an annoying noise, not to mention that it makes me think something bad is going to happen to my latop [and I just bought it].
First of all, is there a way to know which version of the driver the ubuntu OS is using?
Secong, I want to try installing the latest driver (0.9.1 version) [assuming ubuntu dapper isn't using the lastest] so to "see" if it solves the problem but... how do i install it if there is one already installed? [apart from the make and stuff]

---

### Post by Dr. Nick on 2006-07-22
If you didnt have to do anything to set up the wireless in the first place then it is probably using a kernel driver, to update that driver would require you to update your kernel. If you wanted to try the latest, and the latest isnt in the kernel. you would most likely have to do the make install routine. I dont know exactly how to see the current version,

Hopefully someone can help you a bit more with the specific issue

---

### Post by saul_2110 on 2006-07-22
To make it clear... the installation of the OS recognized by itself the wireless card.
But then, if in the kernel is the same version I'm trying to install [with the make install and etc.], would it be dangerous for the system?

---

### Post by Dr. Nick on 2006-07-22
not necessarily dangerous, but probably not usefull. You woluld have to remove/ or move the actual dirver file from inside the kernel directory though, or else it would always get loaded over your built one.

---

### Post by Ptero-4 on 2006-07-22
Get your laptop checked at a technician. If there's something broken your laptop will hopefully still be covered by the warranty.

---

### Post by saul_2110 on 2006-07-23
I thought of that but the warranty says it doesn't covers damage due to software not shipped with the laptop originally... and becouse the problem rarerly presents when running XP, it's gonna be dificult to make the warranty valid.
Though i should give it a try.

---

