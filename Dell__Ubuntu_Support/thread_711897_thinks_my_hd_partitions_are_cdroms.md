---
title: "thinks my hd partitions are cdroms?"
date: 2008-03-01
forum: Dell  Ubuntu Support
---

### Post by freddybob on 2008-03-01
Got a new Dell Inspiron 530n yesterday.  Very very confused.

To begin with it wouldn't boot every time.  1 in 2 attempts would leave it stuck on the black screen where the Ubuntu logo first appears with the progress bar - but the progress bar was stuck.

After a while this bumped me to an initramfs prompt, but the keyboard was registering two key-presses for every key I tried (so I couldn't type 'help' as it came out 'hheellpp').

I tried recovery-mode and it showed errors that said something about ata1.00 retrying after 5 seconds.  (Sorry can't remember the exact words.)

As I said the machine sometimes boots, right now the machine is running but all my partions are /sda not /hda - it looks like I have 4 cd/dvdrom drives when I should only have two (and two hard disk partitions).  What has happened?  Is this a hardware or software error?  Should I just reinstall from scratch?

---

### Post by freddybob on 2008-03-01
tried again in recovery mode and got this...

ata1.00: failed to set xfermode (err_mask=0x40)
ata1: failed to recover some devices, retrying in 5 seconds

---

### Post by freddybob on 2008-03-01
found this suggestion to add 'irqpoll' to /boot/grub/menu.lst

[http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

so far so good

---

### Post by gbrainin on 2008-03-01
The fact that your hard drive partitions are shown as /sda[n] is normal.  The "s" refers to the fact that it is a serial drive, and since the 530n only has SATA connections, your hard drive is serial.  (You would also get an "s" if it were a SCSI drive.  "H" is reserved for the old parallel IDE drives, I think.)

I don't know about your other problems, but if you continue having them, you can try calling Dell's linux support number: 866-622-1947.  _Do not_ call the regular support line, even if you have a 100% hardware problem; they won't know what to do with you.

---

### Post by freddybob on 2008-03-01
Thanks gbrainin.

What I was saying about /hda and /sda is obviously just my lack of understanding of Linux file systems.  Thank you for the explanation.

My machine is still working well with the irqpoll parameter added to the grub list file.  Don't understand why a brand new computer should require it though...

---

### Post by gbrainin on 2008-03-01
You're welcome.

I'm not sure why you should need the irqpoll option, either.  My guess is that there's something in your hardware configuration that isn't responding in a timely fashion (what the kernel considers timely).  My 530n works fine without irqpoll.

---

### Post by freddybob on 2008-03-02
When you say something in my hardware configuration do you think it is a sign of faulty hardware or just that Dell have somehow misconfigured the system?

---

### Post by gbrainin on 2008-03-02
I don't fully understand what irqpoll does, to be honest, but it doesn't necessarily mean that there's something wrong.  It could just be, for example, that some particular piece of hardware takes N microseconds to respond, and the kernel thinks N microseconds is too long so assumes that it's not going to get an answer.  That's not an error per se, just an incompatability that needs a workaround.

However, it wouldn't hurt to do a hardware check.  If you still have the original partitioning from Dell, you should be able to boot into a hardware diagnostics mode.  I forget if you get there via pressing F12 on boot or by a selection in the GRUB menu, but it'll run through some diagnostics and let you know if anything is wrong.  If something does come up bad, again, call the LINUX support line or you may as well bang your head against a wall.

---

### Post by freddybob on 2008-03-04
Thanks again gbrainin, I haven't tried hardware diagnostic mode because I stumbled on what seems to be the root of the problem.

When I plug my USB keyboard into one of the upper two USB ports on the back of the machine it has trouble booting.

When I instead plug it into one of the lower ports it works fine.

---

### Post by gbrainin on 2008-03-04
Well, glad you were able to find your problem.  I have no idea why this should make a difference (perhaps it's the order that the USB controllers are polled?).  Does the machine have problems booting if you plug something else into the upper ports, like the mouse?

For the benefit of anyone else reading this, I checked, and the hardware diagnostic mode was listed both in the F12 and the GRUB menu.  It's a good first check if you think you have hardware problems: the initial scan takes about 10 minutes, and the error codes (if you get any) will be helpful to the support guys.

---

