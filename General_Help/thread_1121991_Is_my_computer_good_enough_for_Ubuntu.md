---
title: "Is my computer good enough for Ubuntu?"
date: 2009-04-10
forum: General Help
---

### Post by Tipped OuT on 2009-04-10
Hi, just yesterday after using Ubuntu for a couple of weeks by Wubi, I decided to make a full switch over to it. Yup, got rid of Windows XP. Recently I upgraded my RAM from 512 MB's to 784 MB's (something like that). Everything is great but sometimes when I'm looking at a youtube video my CPU will kick up and start to over heat unless I exit the web browser. Is this normal? Also, I can't watch youtube videos in full screen without it being choppy. My CPU also kicks up while running other common applications too. Here are my specs:

[B]HP Pavilion Zv5000 
784 MB's of RAM (128 being used by graphics card)
Pentium 4 CPU 3.2 Ghz
ATI Mobility Radeon 9100/9000 IGP[/B]

I'm scared if this keeps happening my CPU is going to fry. Thanks for the help guys.:guitar:

---

### Post by Ericyzfr1 on 2009-04-10
It is strange, I have 3.2Ghz and only 1GB of RAM, your video card seems better than mine. I rarely use more than 500MB of RAM even on youtube ( HD does not work for me).
Did you try to watch the videos with Totem?

---

### Post by khelben1979 on 2009-04-10
1. Your flashplayer could be the slow open source gnash player instead of the one which comes from Adobe.

2. Also, I highly suspect that you're using slow graphics drivers (open source) also. (download fast native drivers directly from ATi)

If you fix the above, you will be able to enjoy YouTube videos with your present computer configuration flawlessly. Your computer is not to slow for Ubuntu.

---

### Post by VCoolio on 2009-04-10
I have 2.4 Ghz, 512 RAM, NVidia 5200, compiz and everything running with no problems whatsoever. Don't have an answer to your problems, but you should be able to run Ubuntu.

---

### Post by Tipped OuT on 2009-04-10
Okay, I think it might be my drivers then. But will someone care to explain how I intsall the drivers from ATI's website. There in ".run" format. Thanks guys.

---

### Post by starcannon on 2009-04-10
Just noticed this is likely a laptop, so, unless you want to do laptop oragami(sic) just try blowing out the ventilation grates in both directions thoroughly with some canned air.

GL

> **Tipped OuT said:**
> Hi, just yesterday after using Ubuntu for a couple of weeks by Wubi, I decided to make a full switch over to it. Yup, got rid of Windows XP. Recently I upgraded my RAM from 512 MB's to 784 MB's (something like that). Everything is great but sometimes when I'm looking at a youtube video my CPU will kick up and start to over heat unless I exit the web browser. Is this normal? Also, I can't watch youtube videos in full screen without it being choppy. My CPU also kicks up while running other common applications too. Here are my specs:

[B]HP Pavilion Zv5000 
784 MB's of RAM (128 being used by graphics card)
Pentium 4 CPU 3.2 Ghz
ATI Mobility Radeon 9100/9000 IGP[/B]

I'm scared if this keeps happening my CPU is going to fry. Thanks for the help guys.:guitar:

You have plenty of muscle (little anemic on ram but still no problem). I recently did a bunch of P4 tune ups, and I would have to say they are a hot little beasty, so be sure to keep the heatsinks clean and clear of dust, hair, dander, and all the other junk that seems to make it into our precious heatsink fins. If this is a desktop computer, I would also recommend getting some Artic Silver thermal compound, and reseating your CPU with that, check that the CPU fan is still rotating fast enough, if not replace it.

Just my .02, GL.
Rob aka starcannon

---

### Post by starcannon on 2009-04-10
> **Tipped OuT said:**
> Okay, I think it might be my drivers then. But will someone care to explain how I intsall the drivers from ATI's website. There in ".run" format. Thanks guys.

Try the Hardware Driver Manager first, this will keep things a bit simpler for you to start with, while they are not the latest greatest drivers, they are usually more than sufficient, and have the advantage of auto updating themselves. You can find the Hardware Driver Manager in:
System>Administration>Hardware Drivers.

GL and have fun.

---

### Post by mb_webguy on 2009-04-10
After you try Hardware Drivers, try installing [EnvyNG]("apt://envyng-gtk").  I'm pretty sure it handles ATI drivers as well as nVidia.  Run it from the terminal using "envyng -t", and follow the simple menu options to have it detect the best driver for your card and install it for you.

---

### Post by Tipped OuT on 2009-04-10
Thanks for the help guys! I'll try it!:p

---

### Post by khelben1979 on 2009-04-10
Or you can just run the ATi driver from a text shell like [xterm]("http://en.wikipedia.org/wiki/Xterm") for example. Don't forget to run it like this:

```
sudo ./[name of the ati driver file]
```

Also, if it won't execute correctly, do this:
```
sudo chmod 777 [name of the ati driver file]
```
(It will change the file attributes to -rwxrwxrwx where r=read, w=write and x=executable)

---

