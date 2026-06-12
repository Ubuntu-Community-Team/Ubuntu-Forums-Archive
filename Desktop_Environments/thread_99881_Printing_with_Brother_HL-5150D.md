---
title: "Printing with Brother HL-5150D"
date: 2005-12-06
forum: Desktop Environments
---

### Post by jyer on 2005-12-06
Hello,
I've been trying to install a Brother HL-5150D for some time now (newbye on linux). I finally succeeded by following the instructions on this website (thanks), namely:

For Debian GNU/Linux I got Duplex printing to work on 5150D viz
  cd  <cdrom>/Driver/PS/PPD/<language>
  sudo cp -i BR5170_2.ppd /usr/share/cups/model/
  sudo killall -HUP cupsd

then goto CUPS interface, and now choose the (new) "HL-5170DN BR-Script3 (en)"
option

Only, there are still two problems.
1. The printer only prints one job. I then have to restart linux to print a second (I tried /etc/init.d/cupsys restart, but it doesn't work). 
2. When I send the first job, the printer starts making noise and then the paper led flashes. I then have to switch from A4 to Legal (or opposite) with the button on the back of the printer. Any ideas?

I've also got another question: how can I set the default printing values so that it always prints two pages per sheet?

Thanks a lot,
jr

---

### Post by dbet on 2005-12-06
jyer,

Try going to the Brother drivers downloads and follow their instructions.  It worked for me like a charm.

Here is the link: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

---

### Post by jyer on 2005-12-07
Hi,
Thanks for the link. Unfortunately I've already tried it and the drivers completly blocked my apt system. I had to reinstall Ubuntu to get it working again...

---

### Post by niceguy123 on 2007-12-03
When I try printing pictures jpg, tif or pdf the following error message is printed:

ERROR NAME;
           ierror
COMMAND;
      fill
OPERAND STACK;

---

### Post by drfox on 2007-12-10
> **niceguy123 said:**
> When I try printing pictures jpg, tif or pdf the following error message is printed:

ERROR NAME;
           ierror
COMMAND;
      fill
OPERAND STACK;

I've solved part of the problem with my Brother MFC-7820N by removing eye of gnome (eog) and evince, and installing KPDF. Now my pdf's print, but I get the same error when I try to print from the web.

HTH.  Larry

---

