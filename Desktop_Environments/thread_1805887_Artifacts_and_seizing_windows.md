---
title: "Artifacts and seizing windows"
date: 2011-07-16
forum: Desktop Environments
---

### Post by kurashu on 2011-07-16
I'm a new convert and recently installed Natty Narwhal on my Dell Dimension 3100 (factory default, specific specs escape me at the moment, but it met everything in the basic requirements). Everything is fine except for what can only be described as my windows seizing and leaving artifacts when I either tab between open ones or open a new process. Or even right after booting up.

For example, when I boot up my computer, after the Ubuntu loading screen, my desktop appears but if I click anywhere on the desktop it's as if I strip it away and the Ubuntu loading screen is underneath. Or if I open up Firefox and then open a folder, Firefox freaks out and despite scrolling down it "seizes" and settles on what I was viewing before or the folder will appear over it despite not being focused on.

I can eventually settle this by Alt+Tab several times but it's annoying at best and usually extremely frustrating, made even more so by my 70 year grandmother I share this computer with (who I had to create a shortcut to her hotmail login on the desktop when this machine ran XP).

I'm unsure if this is a problem with Unity/Gnome (Ubuntu spit out an error saying I didn't have the hardware for Unity when I first booted it up, so I guess I'm running Gnome) or with Narwhal. I'm considering going down to 10.10 Maverick Meercat but only if I really need to.

Being a new convert, I'm unsure what commands I should run to provide information but I'll be more than happy to comply if I'm given the needed ones.

---

### Post by Mr. Shannon on 2011-07-16
The first thing to do is to go to Additional Drivers (under System->Administration-Additional Drivers if using the plain Gnome desktop) and install any proprietary drivers for you video hardware.

If that did not work the next thing I would suggest is to log out and when logging back in choose the Ubuntu Classic (no effects) option for the session.  NOTE: you will need to change this after you click on your name but before you confirm.  NOTE: Since it gave you the inadequate hardware error it is probably booting to this session anyways but it won't hurt to force it to do so.

As a side note, I have had more graphics issues with 11.04 than I did with 10.10.

---

### Post by kurashu on 2011-07-17
I tried both of these and it still acts up. It's probably faulty drivers, I found another person who had the same problem on a different site. I'm going to downgrade and see if that helps. If not, I guess I'm SOL?

---

### Post by wildmanne39 on 2011-07-17
> **kurashu said:**
> I'm a new convert and recently installed Natty Narwhal on my Dell Dimension 3100 (factory default, specific specs escape me at the moment, but it met everything in the basic requirements). Everything is fine except for what can only be described as my windows seizing and leaving artifacts when I either tab between open ones or open a new process. Or even right after booting up.

For example, when I boot up my computer, after the Ubuntu loading screen, my desktop appears but if I click anywhere on the desktop it's as if I strip it away and the Ubuntu loading screen is underneath. Or if I open up Firefox and then open a folder, Firefox freaks out and despite scrolling down it "seizes" and settles on what I was viewing before or the folder will appear over it despite not being focused on.

I can eventually settle this by Alt+Tab several times but it's annoying at best and usually extremely frustrating, made even more so by my 70 year grandmother I share this computer with (who I had to create a shortcut to her hotmail login on the desktop when this machine ran XP).

I'm unsure if this is a problem with Unity/Gnome (Ubuntu spit out an error saying I didn't have the hardware for Unity when I first booted it up, so I guess I'm running Gnome) or with Narwhal. I'm considering going down to 10.10 Maverick Meercat but only if I really need to.

Being a new convert, I'm unsure what commands I should run to provide information but I'll be more than happy to comply if I'm given the needed ones.
Hi, run these command in a terminal
```
sudo lshw
```
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by kurashu on 2011-07-17
I downgraded to Meerkat and it's functioning much better now. Sorry for bothering about this. :/ Thank you for the timely responses though.

---

### Post by wildmanne39 on 2011-07-17
Hi, your welcome! enjoy ubuntu.

---

