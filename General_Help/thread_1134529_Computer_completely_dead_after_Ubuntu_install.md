---
title: "Computer completely dead after Ubuntu install"
date: 2009-04-23
forum: General Help
---

### Post by mxboy15u on 2009-04-23
Yikes! I have had many successful Ubuntu installs. This install onto my aspire one went normally. At the point where it asks to remove the media and press enter I did, it restarted and now wont even boot to a bios screen, won't turn the hard drive won't do anything. I can turn it on and off (the only way to know is that the fan is running and light is on) but my computer is completely bricked. Can anyone help me at least get to the bios screen so I can try another install? Thanks!

---

### Post by miegiel on 2009-04-23
Try resetting the BIOS.

---

### Post by mxboy15u on 2009-04-23
How do I do that? Now the computer will not even shut off when the power button is pressed and held, that was working before.

---

### Post by 3Miro on 2009-04-23
IF you cannot get to BIOS you have a big hardware problem. The BIOS is long before anything Ubuntu is loaded in to the system.

The problem could anything from RAM to Motherboard to CPU to Video. If you feel comfortable disassembling your computer, you can try to disconnect the Video to see if you get a Motherboard warning beep. You can try that with the RAM also. CPU is tricky, unless you don't know what you are doing, don't mess with that (if you know what you are doing you probably know more than me).

The other option is to call the vendor/warranty provider/some computer technician.

---

### Post by 3Miro on 2009-04-23
> **miegiel said:**
> Try resetting the BIOS.

Actually that is what you should try first, my ideas should come second.

---

### Post by miegiel on 2009-04-23
> **mxboy15u said:**
> How do I do that? Now the computer will not even shut off when the power button is pressed and held, that was working before.

It should say in your manual. If you don't have it anymore you usually can find it on the manufacturer's site as a pdf.

btw. You'll need to open your laptop 8)

---

### Post by mxboy15u on 2009-04-23
I am not afraid of opening it up. I am kind of shocked that Ubuntu was able to do this to a computer...I always though nothing could kill the bios. Is that true? Is it possible it was just a coincidence?

---

### Post by cwbar_1 on 2009-04-23
Probably just a coincidence.  If possible, turn computer on an press F2 several times. (do this as soon as the power light is on) If it asks for a password, if you know it, enter the password or just press enter if you haven't password protected the set-up.  If you cannot get in by this method, you will have to "open it up."

---

### Post by miegiel on 2009-04-23
> **mxboy15u said:**
> I am not afraid of opening it up. I am kind of shocked that Ubuntu was able to do this to a computer...I always though nothing could kill the bios. Is that true? Is it possible it was just a coincidence?

I think it was, I hope it was :D If it's not you might have discovered something serious with jaunty.

---

### Post by mxboy15u on 2009-04-23
Ok, with a boot based bios reset (involves holding down keys while pressing power) the bios was reloaded and it is alive!!!! Thank you guys very much!

Jaunty definately bricked my bios on install...I am afraid to do a restart.

Edit: Restart completed successfully. Wow thanks again!

---

### Post by jowilkin on 2009-04-23
I would still chalk this up to a coincidence.  It's very unlikely for an OS install to effect the bios.

---

### Post by bingobingo on 2009-04-26
Just did a upgrade last night now I have a brick on my desk. I thought I had a successful upgrade, I was able to reboot and went into Gnome then I logged out and logged in to KDE to check it if all is well. Then I went to log out again to get back to Gnome when during logout the screen went to BIO page, that was strange. I did not know what to do from there so I shut down the computer. That was the last of my computer, I can no longer boot up at all now. All I get is one beep, thent wo beeps, two more beeps, then three beeps and no screen activation what so ever. I now own a brick. There is no way to reset bios, any help?

---

### Post by miegiel on 2009-04-26
> **bingobingo said:**
> There is no way to reset bios, any help?

There's always a way to reset the BIOS, check your PC's manual for instructions.

---

