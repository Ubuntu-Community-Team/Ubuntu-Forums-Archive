---
title: "Help with monitor interlase mode wanted"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by stoneybroke on 2008-01-14
Hi, I have only been using ubuntu for a short while now and on my other computer I happened to change the screen resolution too high I wasn't given the option of keeping the mode I chose or not and it didn't revert back to normal mode after the normal 15 seconds, after I re-booted the computer the resolution is so bad I can't change it back to normal it looks like 5 screens are on display.

So can anyone tell me what I need to do to get my screen back to 1024 x 768 @ 60hz again.

Thanks in advance, Malcolm

---

### Post by Forlong on 2008-01-14
Run ```
sudo dpkg-reconfigure xserver-xorg
``` and configure it there.

---

### Post by stoneybroke on 2008-01-14
Thanks forlong I have tried that command exactly as you told me to but it didn't work I keep getting error code 27 Unrecognized command even when I tried all other variations it gives the same error. Any ideas?

---

### Post by Forlong on 2008-01-14
Hm... where did you use that command?
In the terminal of your desktop environment? Or in a "maintenance shell" or something like this?
All I found when googling that error seems to have something to with GRUB. :confused:

Sorry, never heard of such a problem before.

---

### Post by stoneybroke on 2008-01-14
I rebooted the computer and used GRUB as I can't get a shell or can I? I don't know I'm only just a beginner with ubunu.

---

### Post by Forlong on 2008-01-14
What entry did you chose in GRUB?

---

### Post by stoneybroke on 2008-01-14
I only entered the commands that you gave me exactly as shown, I have tried running a shell from the startup CD it worked from that but it didn't save the info to the hard drive.

---

### Post by Forlong on 2008-01-14
Yeah, of course it doesn't. 

Well, try booting into the "recovery mode" (that's a GRUB entry) and use the command without the sudo prefix.
(you have to write it down, because that's only an shell)

---

### Post by stoneybroke on 2008-01-14
Ok it worked many thanks for your help I owe you 1 gallon of beer.

---

