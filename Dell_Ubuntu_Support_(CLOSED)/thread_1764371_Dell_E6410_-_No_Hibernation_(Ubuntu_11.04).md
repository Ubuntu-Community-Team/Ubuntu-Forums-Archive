---
title: "Dell E6410 - No Hibernation (Ubuntu 11.04)"
date: 2011-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by A4orce84 on 2011-05-21
Hello Everyone,

I recently installed Ubuntu 11.04 on my Dell E6410 and everything works great. Video, wireless, SD-card reader, etc. My computer is able to suspend with no issues, but I cannot hibernate.

Has anyone else experienced the above problem and found a solution?

Thanks in advance!

--Asif

---

### Post by mikewhatever on 2011-05-21
A possible reason could be that your swap partition is smaller then RAM. If that's the case, you'll need to enlarge it to be able to suspend to disk, aka hibernate.
Can you provide some details about what happens when trying to hibernate.

---

### Post by Soldier2580 on 2011-05-28
Hey, I have the same problem I think, but with a Packard Bell Easynote LJ61. Normally (as in Maverick), when I close the lid, or press the button, the screen goes black and backlight goes out, then I get a red blinking light when the system goes into hibernate. When I try this now, the screen goes black, but the backlight stays on, and the system just keeps on running. Nothing happens after this moment, and i can't do anything except for a hard reboot :/

Thanks for any help!

---

### Post by bubbasmurf on 2011-06-06
I have this exact same problem on my dell desktop (dimension 4700).  I tried TuxOnice but it did not resolve it!  Someone have an answer for this?

---

### Post by Novacaptain on 2011-06-07
You can install an old linux kernel (2.6.35 works for me) if you want suspend/hibernate to work like it should. Then run "sudo update-grub" to get the kernels available from your bootloader menu. The old kernel should be available under previous linux versions.

Other than that I have no clue, there are bug reports filed on launchpad but I dont know if anyone is looking at it.

---

### Post by marzfel on 2011-08-23
I have the same problem, there is simply no hibernate option in my power drop down menu, I do not have a swap partition because for some reason my hard disk wouldn't accept having more than 4 partitions.. I have got one already for the stupid windows (which I need to keep) and 1 for its recovery and its loader. So I have no space for a swap partition, and I would really love it if ubuntu can hibernate. Any suggestions?

---

### Post by emanuelefanton on 2011-08-28
you had to make and estended partition...
the 4 'primary' partition limit is well known.
make the last one extended and inside it make as many partition as you like.

---

### Post by CDSRV on 2011-09-07
there are a few packages to add, but they ended up not working -- system is down with "grub rescue>"

---

