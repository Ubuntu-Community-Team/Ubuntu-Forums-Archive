---
title: "Suse-Ubuntu"
date: 2008-12-13
forum: General Help
---

### Post by Ankurp992 on 2008-12-13
Hey, i have Opensuse 11 (only) istalled on my laptop, and i want to try and switch to Ubuntu. I know that when i installed Suse, i had do it from Windows (which i erased) to open up its CD. My question is how can i install Ubuntu with only Opensuse installed on my CPU. Cuz i know linux cannot open .exe files. Thanks :)

---

### Post by |{urse on 2008-12-13
Okay, your post doesn't make sense on a few points, first off you don't install suse from windows. secondly, you cant install anything on your cpu (central processing unit a.k.a. your processor) thirdly, you can run .exe's under linux with wine. So to answer what im thinking your question is "Can i install ubuntu with suse already on my hard drive?" the answer is yes! Just pop in an ubuntu livecd, reboot your computer and install it. If you have any questions about the install process I will watch this thread and answer as many of them as i can. Welcome to Ubuntu! You'll probably like it a lot better than opensuse!

---

### Post by Ankurp992 on 2008-12-13
> **|{urse said:**
> Okay, your post doesn't make sense on a few levels, first off you don't install suse from windows. secondly, you cant install anything on your cpu (central processing unit a.k.a. your processor) thirdly, you can run .exe's under linux with wine. So to answer what im thinking your question is "Can i install ubuntu with suse already on my hard drive?" the answer is yes! Just pop in an ubuntu livecd and install it.

can i install it with the regular DVD version? Like downloading it as an iso, burning it and etc?

---

### Post by ugkbunb on 2008-12-13
> **Ankurp992 said:**
> can i install it with the regular DVD version? Like downloading it as an iso, burning it and etc?

yup burn it and then just set your drive your boot order to boot from your dvd-rom before your hard-disks

---

### Post by Ankurp992 on 2008-12-13
> **ugkbunb said:**
> yup burn it and then just set your drive your boot order to boot from your dvd-rom before your hard-disks

sorry im super noob when it comes to installing new OS's how exactly do you set a drive into a boot order? :) lol

---

### Post by |{urse on 2008-12-13
Good Lord, dont be sorry! The fact that you don't need/want windows anymore makes you no longer a noob =)

---

### Post by |{urse on 2008-12-13
The boot order is mainly set in the BIOS. Yours is already set correctly (because im psychic and i know it is 0o0o0o0o) Just burn that iso, pop that badboy in and let us know if you need help, you probably wont, it's very straightforward.

---

### Post by |{urse on 2008-12-13
O snap do you need to know how to burn an .iso under opensuse 11? Open a terminal and type

```
yast -i k3b
```

then type

```
k3b
```

then look in the actions menu. Select burn disc from image. Then browse to the ubuntu image that you downloaded. You'll figure the rest out easy. ):P

---

### Post by Ankurp992 on 2008-12-13
> **|{urse said:**
> O snap do you need to know how to burn an .iso under opensuse 11? Open a terminal and type

```
yast -i k3b
```

then type

```
k3b
```

then look in the actions menu. Select burn disc from image. Then browse to the ubuntu image that you downloaded. You'll figure the rest out easy. ):P

lol dont worry, i have a windows too thats where i do all my iso stuff. But if i do have any problems installing ill post back, thanks for your guys help :)

---

### Post by Ankurp992 on 2008-12-13
okay i am having a problem lol, I put the disk in my laptop (suse) and nothing comes up and it doesnt acknoledge a disk being in there. I put the disk in my windows and the ubuntu istallion screen pops up. What should i do?

---

### Post by |{urse on 2008-12-14
You are supposed to put the disk in and restart it ( the laptop ) 

If i am not in fact psychic and your boot order is set incorrectly do this 

If you have not yet tried rebooting your laptop with the disk in, go do it, ignore the rest of this post unless you dont get ubuntu running. 

while the laptop is booting (about 2 seconds after powering on the laptop) hit the Delete, f1, f2, and f8 keys (in sucession, not at the same time) Repeat hitting these keys a couple times. If you are able to get into your bios look for a section called "Boot Order" and be sure that your cd/dvd drive is set to boot first. You would be wise to make very sure that nothing other than the boot order is changed before you save your settings. 

*or you could tell me what make and model of laptop you have. I could probably find you a link with more specific instructions as it depends on the bios version (which varies among different mainboard manufacturers) what instructions to give you to find the boot order option.

---

