---
title: "unexpected IRQ trap"
date: 2009-03-16
forum: General Help
---

### Post by triplemaya on 2009-03-16
This problem is filling up the log files on my computer so fast that they take up gigabytes and fill up the hdd periodically.
This started when I intalled nvidia drivers for an nvidia graphics card.


Mar 16 20:28:46 pc-2 kernel: [  290.511377] unexpected IRQ trap at vector 9b
Mar 16 20:28:47 pc-2 kernel: [  291.515515] irq 155, desc: c04a0b00, depth: 1, count: 0, unhandled: 0
Mar 16 20:28:47 pc-2 kernel: [  291.515523] ->handle_irq():  c0177250, handle_bad_irq+0x0/0x2a0
Mar 16 20:28:47 pc-2 kernel: [  291.515535] ->chip(): c0477180, no_irq_chip+0x0/0x40
Mar 16 20:28:47 pc-2 kernel: [  291.515541] ->action(): 00000000
Mar 16 20:28:47 pc-2 kernel: [  291.515543]   IRQ_DISABLED set

googling for unexpected IRQ trap doesn't seem to bring up anything useful / comprehensible at my level.

I've tried all the drivers which are compatible, 177, 173, 96 and I'm now on 180, but the IRQ problem is there with all of them.
Card is an Asus Vga En7300le/td/128mb Pcie Dvi Gf7300le

---

### Post by kuja on 2009-03-17
This is a very nasty problem. Probably as bad as they come. This page seems to be worth looking at, but it doesn't seem to be "solved" either ... [http://www.debianhelp.org/node/8167](http://www.debianhelp.org/node/8167)

Good luck. You'll probably need it.

---

### Post by triplemaya on 2009-03-17
Thanks for the link. Their problems seem to be to do with boot up whereas mine happens all the time.
I'm now contemplating getting a different graphics card as a cheap solution!
On the other hand, the system seems to run perfectly well, and now I have a cron job to delete the log files there doesn't seem to be a real problem, but is this just inserting head in sand?!

---

### Post by kuja on 2009-03-17
Yeah, so long as it's actually working you probably shouldn't do anything **too** drastic about it. The last thing you would want to do is make something worse right? If you don't generall use the logs to start with you might be able to turn off logging by disabling the kernel log daemon. An easy way of accomplishing this is to install/run sysv-rc-conf and disabling klogd on all runlevels. I've never tried that before though so I don't know how well that would work.

I hope the new video card helps, but seeing as it's an IRQ issue (motherboard problem I think) I have doubts as to whether it will.

---

### Post by triplemaya on 2009-03-17
Thanks for that.

The problem only exists when the graphics card is installed, when it is removed and the pc boots with only the onboard grahpics there's no problem.

I would very much like to go back to just using the onboard graphics, but this is not an available option!? Everything was fine before I tried out this new graphics card, but having played about with drivers and so on no matter what I do I cannot get the resolution up to a reasonable usable setting with the onboard graphics, the only available options seem to be live with what I've got or reinstall the operating system!

---

### Post by kuja on 2009-03-17
Try removing the card and then backing up and removing your /etc/X11/xorg.conf file (yes, it's safe to do that since 8.04). By default there is little or no xorg.conf file anyway nowadays, and it will detect things by itself if the file doesn't exist. Worth a try anyhow.

---

### Post by triplemaya on 2009-03-18
Thanks for the suggestion, but I have been there, done that, got the t shirt! Many hours have been spent with every kind of variation of removing and editing xorg.conf, including installing on another hdd, getting the graphics resolution correct, and copying that xorg.conf to the current set up. It *really* doesn't want to!

---

