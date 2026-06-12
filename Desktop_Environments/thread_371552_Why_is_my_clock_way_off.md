---
title: "Why is my clock way off?"
date: 2007-02-27
forum: Desktop Environments
---

### Post by Quillz on 2007-02-27
In my time zone right now (GMT -08:00) it's 0:02. My clock in the taskbar, however, says it's 16:00, which is obviously not right. I have NTP installed, so it should be by automatically syncing with a number of time servers. I also have my correct time zone selected. Strangely enough, if I show UTC time instead, it's correct. It was working fine when I first installed Ubuntu, and messed up at some point. What should I do?

---

### Post by PaulFXH on 2007-02-27
CMOS battery?

---

### Post by Quillz on 2007-02-27
> **PaulFXH said:**
> CMOS battery?
What is this? How would I check it?

---

### Post by PaulFXH on 2007-02-27
The CMOS battery is a small Lithium battery generally located on your motherboard. You will need to open the computer casing and you should see a small (~ 1cm diameter) silver battery (shaped like a coin).
This battery is needed for the computer clock to stay accurate. When the battery is on the way out, the clock will give crazy times.
A replacement battery is very cheap and can generally be purchased even in a supermarket.
However, if you haven't done this before, you will need to be careful in opening up your computer and avoid touching any of your chips. I would advise checking your computer manual for "Change CMOS battery" or something. Also you could google for the precautions necessary.
Good luck.

---

### Post by Quillz on 2007-02-27
> **PaulFXH said:**
> The CMOS battery is a small Lithium battery generally located on your motherboard. You will need to open the computer casing and you should see a small (~ 1cm diameter) silver battery (shaped like a coin).
This battery is needed for the computer clock to stay accurate. When the battery is on the way out, the clock will give crazy times.
A replacement battery is very cheap and can generally be purchased even in a supermarket.
However, if you haven't done this before, you will need to be careful in opening up your computer and avoid touching any of your chips. I would advise checking your computer manual for "Change CMOS battery" or something. Also you could google for the precautions necessary.
Good luck.
It can't be this. First off, I'm running Ubuntu on a virtual machine, and secondly, the host computer, an iMac, is only two weeks old. It has to be something else.

---

### Post by ComplexNumber on 2007-02-27
Quillz
have you checked Time and Date settings? go to main menu -> system -> administration -> time and date.
maybe its your time zone that has changed somehow. its happened to me before on another distro. you can synchronise it with internet servers.

---

### Post by Quillz on 2007-02-27
> **ComplexNumber said:**
> Quillz
have you checked Time and Date settings? go to main menu -> system -> administration -> time and date.
maybe its your time zone that has changed somehow. its happened to me before on another distro. you can synchronise it with internet servers.
As I've already stated, I have the correct time zone (Los Angeles, GMT -08:00), and NTP support is already installed. I can't "Synchroize Now" because that options is grayed out. So, is there a terminal command that will force a sync? Also, UTC displays the correct time, but as soon as I uncheck that option, the incorrect time continues to be displayed. This is a fairly major problem for me, because it whenever a file is modified on my system, the wrong time is shown.

---

### Post by Winterfresh on 2007-02-28
Give this a try:

[http://doc.gwos.org/index.php/Setting_Local_Time]("http://doc.gwos.org/index.php/Setting_Local_Time")

---

### Post by Quillz on 2007-02-28
I'll try this, thanks.

---

### Post by newlinux on 2007-02-28
if you uncheck the box that says "Keep clock synchronized..." you will have the option of synchronizing now - then you can re-check the keep synchronized...

---

### Post by Quillz on 2007-02-28
> **newlinux said:**
> if you uncheck the box that says "Keep clock synchronized..." you will have the option of synchronizing now - then you can re-check the keep synchronized...
I was considering this, but it would be a pain for this to occur every startup. I'm going to try the other method first, and if nothing comes of it, I'll try the manual configuration instead.

---

### Post by newlinux on 2007-02-28
> **Quillz said:**
> I was considering this, but it would be a pain for this to occur every startup. I'm going to try the other method first, and if nothing comes of it, I'll try the manual configuration instead.

what time does your hardware clock have? just curious. I had a similar problem and it was my mobo battery, but I imagine it could be a lot of things. The batter itself wasn't bad, but the connection to the mobo was bad. some aluminum and tape fixed it... It only happened when I also unplugged the computer from an outlet.

And yes it is a pain. i would reset the the system clock and hardware clock each boot. But i only rebooted once in a while...

---

### Post by lavinog on 2007-02-28
> **newlinux said:**
> The batter itself wasn't bad, but the connection to the mobo was bad. some aluminum and tape fixed it... It only happened when I also unplugged the computer from an outlet.

you used aluminum and tape on your motherboard?
I would recommend soldering that before the tape falls off and shorts out something.

I doubt that this would be the case for Quillz, but I had a similar problem with my Dell laptop where anytime I went into the bios my clock would get reset. If I don't go into bios the clock is fine even with ntp off. It started doing it when I updated my bios to the lasted rev so i assumed it had something to do with the bios update.

---

### Post by igknighted on 2007-03-01
There is an option somewhere near where you adjust the time that lets you check if your hardware clock is set for UTC.  Since yours obviously is not, you need to uncheck it.  I think Ubuntu defaults to hardware clock using UTC.

---

### Post by Quillz on 2007-03-01
> **newlinux said:**
> if you uncheck the box that says "Keep clock synchronized..." you will have the option of synchronizing now - then you can re-check the keep synchronized...
I finally tried this option and it worked. Now local time shows just that, while UTC shows a time about eight hours ahead, so I assume it's equivalent to GMT. Thanks for the help.

---

### Post by newlinux on 2007-03-01
> **lavinog said:**
> you used aluminum and tape on your motherboard?
I would recommend soldering that before the tape falls off and shorts out something.

I doubt that this would be the case for Quillz, but I had a similar problem with my Dell laptop where anytime I went into the bios my clock would get reset. If I don't go into bios the clock is fine even with ntp off. It started doing it when I updated my bios to the lasted rev so i assumed it had something to do with the bios update.


The tape is to keep the battery in contact with the aluminum, not the aluminum to the mobo. I'm not soldering the battery to the aluminum, and the way the tape is put on it isn't going to fall off of anything.

Glad that worked for you Quillz. doesn't seem like that solved the problem of why it happens in the first place, but at lease you have a workaround.

---

