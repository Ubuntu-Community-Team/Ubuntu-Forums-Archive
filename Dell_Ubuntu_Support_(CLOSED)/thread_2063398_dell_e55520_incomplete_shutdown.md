---
title: "dell e55520 incomplete shutdown"
date: 2012-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zenlunatic on 2012-09-27
My Dell Latitude E5520 will not shutdown correctly.  Using the GNOME panel default shutdown method everything goes well and my session ends, however shutdown will not pass the last two shutdown icon indicators on the purple shutdown screen.  This is a default 12.04 clean install.

---

### Post by zenlunatic on 2012-09-29
For future reference and the interest of others, logging out then shutting down should go smoothly.  There must be a service that isn't cooperating or something.

---

### Post by daslinkard on 2012-10-02
Does it shutdown correctly if you run the following command?
```

sudo shutdown -h now
```

---

### Post by Rev. Dead Corpse on 2012-10-08
I'm having a similar issue. 12.10 Beta 2. Machine is a stock Dell Optiplex 755.

'sudo shutdown -h now' works fine. 'sudo init 6' hangs right after unmounting any volumes. Looks like it isn't sending the correct warm-boot signal to the ACPI.

Same behavior from the Menu options as well. Shutdown works fine, Restart does not. 

If you don't hit the Escape key during shutdown, it will cycle through the thermometer buttons a couple times and stick with the last one or two not lit. Hitting Escape shows the processes ending normally until it hits that last one.

---

### Post by daslinkard on 2012-10-08
> **Rev. Dead Corpse said:**
> I'm having a similar issue. 12.10 Beta 2. Machine is a stock Dell Optiplex 755.

'sudo shutdown -h now' works fine. 'sudo init 6' hangs right after unmounting any volumes. Looks like it isn't sending the correct warm-boot signal to the ACPI.

Same behavior from the Menu options as well. Shutdown works fine, Restart does not. 

If you don't hit the Escape key during shutdown, it will cycle through the thermometer buttons a couple times and stick with the last one or two not lit. Hitting Escape shows the processes ending normally until it hits that last one.

What happens when you do the following sudo command:
```

sudo reboot
```

Does it restart properly then?

---

### Post by Rev. Dead Corpse on 2012-10-09
> **daslinkard said:**
> What happens when you do the following sudo command:
```

sudo reboot
```

Does it restart properly then?

No. Same behavior as hitting the "Restart" button or a sudo init 6.

Only way to restart it without it hanging is to do a full power off shut down.

---

### Post by Rev. Dead Corpse on 2012-10-09
Just had this happen on a second Dell. Same model.

A 3rd Dell, also same model, is restarting normally. 

Using same 12.10 Beta 2 disk to load them all.

Now I'm really confused...

---

### Post by daslinkard on 2012-10-10
> **Rev. Dead Corpse said:**
> Just had this happen on a second Dell. Same model.

A 3rd Dell, also same model, is restarting normally. 

Using same 12.10 Beta 2 disk to load them all.

Now I'm really confused...
Do not feel bad....my wife's desktop which is a Dell Optiplex is doing the exact thing as yours.....I will be working on this at some point in time tomorrow and once I have a solution I will post the fix on here.

---

### Post by zenlunatic on 2012-10-14
OP here.

Funny thing is my machine is "ubuntu certified" albiet with 11.10...  which means a newer version has broken functionality.  Should have went with system76...

---

