---
title: "Printing via LPR on Terminal"
date: 2009-10-12
forum: Desktop Environments
---

### Post by ruimrcabral on 2009-10-12
Hi all, 

I am doing some testing on a printer and I need to send a job via lpr to the printer. The printer is on the network but not installed on my ubuntu9.04. The printer is not in CUPS aswell.

I have tried the following:
lpr -P "ip" "file" -- Error The printer or class not found
lpr -P "ip:@" "file" -- Error The printer or class not found

lp -h 13.219.14.187:lp 'File' -- Error Scheduler not responding.

Anyone can help?

---

### Post by wojox on 2009-10-13
You need to install the print driver.

---

### Post by ruimrcabral on 2009-10-13
> **wojox said:**
> You need to install the print driver.

Alright.
sorry for my ignorance...why it would not send it to the ip address as prn our ps file?

Rui

---

