---
title: "OS won't load!"
date: 2009-02-20
forum: General Help
---

### Post by AlexLuckett on 2009-02-20
Hello,

I've just recieved a copy of the Ubuntu & Kubuntu CD's. Now I have installed Ubuntu off of the CD, using the option: "Install Within Windows". Now the OS is said to install correctly. It tells me to reboot my laptop - so I do so. When my laptop then reloads, it tells me which OS to load up as it should (Windows Vista or Ubuntu).

I select the Ubuntu option and it appears to start. But as soon as it has started, a black screen displays with a flashing "_"  in white. I've left it for about 15 minutes, and still that screen appears.
I've unistalled it and tried to do the same process - but it just keeps displaying the same results.

Can anybody tell me why this will not load? And how to fix it? Just some information you might need to know:

My laptop is a Dell Inspiron 1712, my hard drive is also configured as RAID 0. I've got all of the minimum requirements for running Linux. I've ran Ubuntu/Kubuntu with the live CD witout installing, and that works fine.

I've also tried the same steps with Kubuntu, with no prevail and the same results. Vista still loads perfectly.

Thanks!
Alex Luckett

---

### Post by fjgaude on 2009-02-20
Likely it is the raid0 that doesn't work correctly with the Ubuntu install. It is likely trying to run from the wrong drive, the one that doesn't have **grub** installed.

I don't know of anyone who has done what you are trying, but I think it can be made to work. Lots of things to learn though.

---

### Post by Therion on 2009-02-20
> **AlexLuckett said:**
> ... my hard drive is also configured as RAID 0.
Why, exactly? 

And yes, as above, this could very well be your problem.

---

### Post by AlexLuckett on 2009-02-20
> **fjgaude said:**
> Likely it is the raid0 that doesn't work correctly with the Ubuntu install. It is likely trying to run from the wrong drive, the one that doesn't have **grub** installed.

I don't know of anyone who has done what you are trying, but I think it can be made to work. Lots of things to learn though.
Thanks for your help, it's really appriciated. Do you know of any way to make it run off the correct drive?
> **Therion said:**
> Why, exactly? 

And yes, as above, this could very well be your problem.
My hard drive was configured as that by default when I purchased my laptop.

---

### Post by fjgaude on 2009-02-20
Well, you will have to learn to use some command line stuff. But since you can't load Ubuntu directly you will have to use the LiveCD. Do that, then run this:

```
fdisk -l
```

From the results you should see two drives and their names, e.g., /dev/sda and /dev/sdb. Show us the results.

Then you can run from the LiveCD this:

```
grub /dev/sda
```

```
grub /dev/sdb
```

Then reboot and see if Ubuntu loads correctly.

Let us know what happens, please.

---

### Post by AlexLuckett on 2009-02-20
> **fjgaude said:**
> Well, you will have to learn to use some command line stuff. But since you can't load Ubuntu directly you will have to use the LiveCD. Do that, then run this:

```
fdisk -l
```

From the results you should see two drives and their names, e.g., /dev/sda and /dev/sdb. Show us the results.

Then you can run from the LiveCD this:

```
grub /dev/sda
```

```
grub /dev/sdb
```

Then reboot and see if Ubuntu loads correctly.

Let us know what happens, please.

Hi there, thanks for the help. I typed in fdisk -l and it told me that cannot load /dev/sda & /dev/sdb.

I then proceeded and typed in grub /dev/sda & grub /dev/sdb. I then rebooted my laptop and it still came up with the same error that I got in the first place.

---

### Post by fjgaude on 2009-02-20
I'm at a loss to suggest something... maybe someone else here can help.

---

### Post by AlexLuckett on 2009-02-20
> **fjgaude said:**
> I'm at a loss to suggest something... maybe someone else here can help.

You did mean to run those commands off the Ubuntu/Kubuntu terminal, if I am correct?

---

### Post by fjgaude on 2009-02-20
Yes, a terminal, one way or another.

I don't understand how fdisk -l would come back with a notice that it can't load a partition. Strange.

What kind of terminal are you using? The one from LiveCD?

---

### Post by AlexLuckett on 2009-02-21
> **fjgaude said:**
> Yes, a terminal, one way or another.

I don't understand how fdisk -l would come back with a notice that it can't load a partition. Strange.

What kind of terminal are you using? The one from LiveCD?

Yes, I am using the LiveCD Terminal. I'll try again and write down exactly what it says.

Thanks!

---

