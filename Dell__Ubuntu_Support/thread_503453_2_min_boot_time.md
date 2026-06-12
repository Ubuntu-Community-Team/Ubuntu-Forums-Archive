---
title: "2 min boot time"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by odius on 2007-07-17
I have a dell dimension 2400. Installed ubuntu studio which went fine. When I boot I get the ubuntu studio splash and hangs for 1.15 minutes. I think it has to do with the on board video card, being intel's 3d extreme graphics (unfortunately) 

here is the boot-chart file

[http://www.zea.ca/bootchart.png]("http://www.zea.ca/bootchart.png")

thx

---

### Post by tekkenlord on 2007-07-18
Can you please attach the /etc/dhcp3/dhclient.conf file? I may have a solution.

---

### Post by odius on 2007-07-18
[http://www.zea.ca/dhclient.conf]("http://www.zea.ca/dhclient.conf")

---

### Post by tekkenlord on 2007-07-18
Thanks. Ok, first of all, edit the line where it says 

timeout 30;

and do it 

timeout 3;

This will reduce your boot time by approximately 30 seconds. 

Second, I saw from your bootchart that the scsi_eh_1 takes a lot of time to load. Take a look at this link: [http://ubuntuforums.org/showthread.php?t=258270](http://ubuntuforums.org/showthread.php?t=258270)

Give the command "top" from a terminal (without the quotes) and see how much cpu is the scsi_eh_1 using. After that, I suggest you try:

killall scsi_eh_1

from a terminal.

Let me know how it goes.

---

### Post by odius on 2007-07-18
Thanks for the help.

I found the solution here [http://ubuntuforums.org/showthread.php?t=416719&page=2]("http://ubuntuforums.org/showthread.php?t=416719&page=2")

adding irqpoll to the kernel entry in /boot/grub/menu.lst work for me, sorry i guess I was looking for a video error??? better just look at the graph next time!

thx

---

