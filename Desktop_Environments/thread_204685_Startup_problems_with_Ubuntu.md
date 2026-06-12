---
title: "Startup problems with Ubuntu"
date: 2006-06-27
forum: Desktop Environments
---

### Post by khdx on 2006-06-27
Hello

I have installed ubuntu off the alt CD on my dimension 2350 with FX5200 vid card.  When I start it up it freezes at the loading hardware drivers splashscreen.  When I add noapic, I get a Kernel not syncing error, then it freezes (can't do ctrl c).  I try to boot on the ubuntu live cd, but I get the same error booting off the live cd.

I tried to get help from someone on alpha.qunu.com and we spent a while to see if I had everything installed correctly, ie correct cd and all that.  He said that everything was correct but was a problem with my hardware.

I have read around the forms and have seen others having the same problem with the 2350 Dimension and FX5200 but have not seen a fix.  Can anyone help me with my problem (I am a newbie at linux so I don't understand all the technical terms yet but am willing to learn)

Thanks
Kevin

---

### Post by khdx on 2006-06-27
Selfish bump, can anyone help?

---

### Post by jamesford on 2006-06-27
i also get this at the loading harware step sometimes, i have a hunch its my audigy2 soundcard but i dont know

---

### Post by khdx on 2006-06-27
Update

I tried enabling the onboard video card and starting the machine with that instead of the FX5200 vid card.  It boots except X11 isn't configured correctly.

So I booted in recovery mode and got to the command prompt.  Now I need help with configuring xorg at the command prompt.  I don't know how to paste the contents in it since I can't save it anywhere.

Can I get some help with this?

Thanks

---

### Post by Steven_B on 2006-06-27
First, back up your xorg.conf:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Then, use Vim to edit it:
```

sudo vim /etc/X11/xorg.conf

```
When Vim comes up, press "i" to get be able to edit the file.
When you are done, press "escape" and then type:
```
:save xorg.conf
```
The colon at the beginning is important!
Hope this is helpful.

---

### Post by khdx on 2006-06-27
X11 fails to start.  I installed ubuntu with my FX5200 graphics card plugged in.  When I start ubuntu up it freezes at loading hardware drivers.  With noapic added on, it comes up with a Kernel not syncing.

So I disabled the FX5200 card in bios and started ubuntu up with the onboard vid card.  It starts up, but doesn't load X11 (says X11 fails).  I would like to get the FX5200 card up and running but I'm not really sure how.  I can get to the /ect/X11/xorg.conf file and open it but not sure where to go from here.  

Thanks

---

### Post by Steven_B on 2006-06-27
could you post your xorg.conf?  It sounds like it may be partly configured for your new graphics card, which won't work for your onboard card.

---

### Post by khdx on 2006-06-27
How do I post it, I don't know how to save it then access it so I can post it on the internet.


Thank
Kevin

---

### Post by Steven_B on 2006-06-27
How are you getting online now?  If it is via dual-boot, can you copy it to a windows-readable part of your drive?
Do you have a floppy drive, and can you read floppies from the computer you get online with?  If so, put a floppy in the linux box, and type:
```
sudo mount /dev/fd0 /media/floppy
sudo cp /etc/X11/xorg.conf /media/floppy

```
What on-board graphics card do you have?  The ATI card drivers can be a pain, so I recommend trying to get the onboard card working first.

---

### Post by khdx on 2006-06-27
I have ubuntu up and running with the onboard video (reinstalled with onboard video).  Now I want to configure my FX5200 to work with ubuntu.  

How do I get linux to see my FX5200?  I am new to linux so I am not all that familiar with what I'm doing.

Thanks
Kevin

---

