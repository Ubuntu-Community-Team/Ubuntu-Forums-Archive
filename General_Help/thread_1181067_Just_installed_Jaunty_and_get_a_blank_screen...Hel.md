---
title: "Just installed Jaunty and get a blank screen...Help!"
date: 2009-06-07
forum: General Help
---

### Post by oxf on 2009-06-07
I've previously ran Hardy 8-04 without any problem. I just installed Jaunty 9-04 and everything went fast and fine finishing with "remove CD" and "restarting sytem". Everyting was fine and started to configure and set things up etc.  Then I shut the PC down.
 
Now I've come back and when I boot up have problems. Grub is fine. I do get an initial error message though "MS Bios bug....8254 timer not connected to IO-APIC"
It obviously is booting because I get the Ubuntu boot up music. But beyond that a totally blank dark screen. Very occasionally it will go through and I get the normal desktop but thats a rarity.
 
Any ideas how to sort this? I assuming I'm going to have to do something booting from the Live CD?
 
Thanks
 
Acer Aspire L100
Chipset NVidea nforce 410 
Video card Nvidea GEforce 6150LE

---

### Post by Old_Grey_Wolf on 2009-06-07
You probably need to update your BIOS. You will need to learn how to flash your BIOS. 

In the meantime, you could try going into the BIOS settings at bootup and disabling IOAPIC.

---

### Post by oxf on 2009-06-07
> **Old_Gray_Wolf said:**
> You probably need to update your BIOS. You will need to learn how to flash your BIOS. 

In the meantime, you could try going into the BIOS settings at bootup and disabling IOAPIC.

OK uhmm.... a couple of questions then. 
What is IO-APIC?  Input/output something or other I presume. Is this definately related to my problem of blank screen at boot up?

Also I just booted from the live CD and went to System>Admin>Hardware Drivers and found none of the 3 propriety NVidea drivers were enabled. I enabled the recomended one (version 180) and rebooted. However, this didn't resolve it.

So is flashing my Bios the likely resolution to the problem or can it be resolved with the right drivers?

Thanks

Acer Aspire L100
Chipset NVidea nforce 410 
Video card Nvidea GEforce 6150LE

---

### Post by Old_Grey_Wolf on 2009-06-07
I am not going to be very helpful because I am not familiar with the problem you are having. Here is a link that may explain the problem to you better than I can  [http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/](http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/)

---

### Post by oxf on 2009-06-07
> **Old_Gray_Wolf said:**
> I am not going to be very helpful because I am not familiar with the problem you are having. Here is a link that may explain the problem to you better than I can  [http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/](http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/)

OK many thanks for that. Appreciate it! It turns out Acer do have a BIOS update for my PC. I'll do that if I can be absolutely sure thats the route of the problem. 

After having read that link I'm somewhat less than convinced for several reasons:
1. I ran Hardy without any problem
2. A lot of the people reporting problems in that link had trouble booting from Live CD . I dont!
3. The Kernal in 9-04 would have been compliled well after my motherboard was produced.

However, that said I never got this error before on Hardy either. I'm no expert on this as well. So....if anyone else has  any thoughts on this problem I really like to hear them. Specifically IS the BIOS bug error on boot up directly linked to me getting a blank screan afterwards?

---

### Post by oxf on 2009-06-08
OK if anyone else has any thoughts on this problem PLEASE do let me know!!

Just to reiterate when I run it from the Live CD everything displays and functions perfectly, no inckling of any problem. (I still get the "Bios bug.." msg on boot up but doesnt affect anything, So for that reason I not sure its the cause of my problem?)

So any ideas?????

---

### Post by oxf on 2009-06-09
Bump..

---

### Post by ktmom on 2009-06-11
You indicate you have a nVidia graphics card.  I think [this thread]("http://ubuntuforums.org/showthread.php?t=1174194") may give a hand.

---

