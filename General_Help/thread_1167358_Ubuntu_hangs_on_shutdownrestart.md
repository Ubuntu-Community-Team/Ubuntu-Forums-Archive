---
title: "Ubuntu hangs on shutdown/restart"
date: 2009-05-22
forum: General Help
---

### Post by miocene on 2009-05-22
I apologise if this is too many topics in a short space of time (my 3rd today) but Ubuntu is going really well bar a few niggling issues I would like to sort out.

when I shut down or reboot Ubuntu it seems to work ok and the "unloading bar" thingy comes and completes and it then says: "shutting down" or "restarting" and a curser just sits there and flashes and nothing happens...

The only way to get it to do anything is to hold power down to force shutdown.

It's not a huge problem but would be nice to have everything working well..

cheers for any help

---

### Post by miocene on 2009-05-25
anybody?
sometimes it says something about USB not found and repeats that line about 10-15 times before saying "restarting system" and blinking away...

---

### Post by Wiebelhaus on 2009-05-25
I've seen this as well and I'm sorry I'm not certain the cause but I'm positive it is related to a device or service that's busy and refusing or is unready to relinquish whatever it's using back to the system for shutdown.

---

### Post by colau on 2009-05-25
To miocene
What is the first boot device selected from bios?

---

### Post by miocene on 2009-05-25
> **colau said:**
> To miocene
What is the first boot device selected from bios?

My DVD drive, then the Ubuntu hard disk

---

### Post by colau on 2009-05-25
Try reinstalling ubuntu 9.04 .

---

### Post by internalkernel on 2009-05-25
You wouldn't happen to have an ATI video card would you? 

I had a similar issue on my laptop, something with the way ATI interacts with the bios and ACPI - it would sometimes hang on shutdown. It's a safe situation to hold the power button, since all the filesystems are unmounted and most services are already killed. 

In my situation, the laptop would come to a complete freeze... no response from capslock or num lock. You could try hitting CTR+ALT+DEL when you're sitting there, see if it responds to anything...

---

### Post by internalkernel on 2009-05-25
> **colau said:**
> Try reinstalling ubuntu 9.04 .

I just have to ask... why? How could a re-install help this situation?

---

### Post by raymondh on 2009-05-25
Hello Miocene,

Just gathering my thoughts and ideas about your thread... and out of curiosity ... what happens when you type (in terminal)

```
sudo shutdown -P 0
```

?

Regards,

---

### Post by miocene on 2009-05-25
> **colau said:**
> Try reinstalling ubuntu 9.04 .
I don't think so... it's taken me long enough to set it up the way I want and install MS Office etc.


[QUOTE=raymondhenson]
Hello Miocene,

Just gathering my thoughts and ideas about your thread... and out of curiosity ... what happens when you type (in terminal)

Code:

sudo shutdown -P 0

?

Regards, [/QUOTE]

That shut it down fine.... now how do I get it to do that every time??

---

### Post by colau on 2009-05-25
> **miocene said:**
> I don't think so... it's taken me long enough to set it up the way I want and install MS Office etc.




That shut it down fine.... now how do I get it to do that every time??

What's the result?
```

sudo reboot

```
```

sudo halt

```

---

### Post by raymondh on 2009-05-25
> **miocene said:**
> 
That shut it down fine.... now how do I get it to do that every time??

Then we know Ubuntu is shutting down in sequence and properly.

-Is this an old or new machine?  
-Have you been playing around with your BIOS settings particulalrly power management?  
-Can you check (in BIOS) if you have acpi activated and then boot and try to shut down? 

Let's make sure BIOS is OK before we go to the  /etc/modules and boot/menu/lst 

Also, backup now and if possible, save an extra copy of your files somewhere outside your system.  I'm hoping we don't have to edit the modules files or the boot menu list.  Anytime we do that, there is a chance of borking the installation.

Also ... this comment of yours is interesting

*sometimes it says something about USB not found and repeats that line about 10-15 times before saying "restarting system" and blinking away..*

How do you connect to the internet?  Is there an external thumb drive/hard drive connected which uses the machines' power to shut down?

Sorry for so many questions ... am just trying to get as much info as possible.

I have to go a memorial day party with the kids .... will check back this thread in about 4-5 hrs.


Regards,

---

