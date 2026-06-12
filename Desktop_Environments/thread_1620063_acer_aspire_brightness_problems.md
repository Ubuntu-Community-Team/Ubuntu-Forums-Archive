---
title: "acer aspire brightness problems"
date: 2010-11-12
forum: Desktop Environments
---

### Post by nsus on 2010-11-12
hello all,

I've recently installed ubuntu 10.10 alongside windows vista as a dual-boot on both of my computers.  This question pertains to my acer aspire 5735Z.  I'm quite new to ubuntu, so I'm sure I'll be needing a lot of help.
I've been having problems with the screen brightness and the screen brightness application.  When first installed I had no problems at all, but now the screen seems to be locked at around 50% brightness.  When I click on the screen brightness application icon on the panel and try to change the brightness, my mouse cursor freezes and/or moves verrrry slowly for 30-90 seconds, then comes back to normal.  Key commands are also suspended after attempting to adjust brightness.
I've tried adjusting the 'power management preferences', and have the display brightness set to 100%, but the screen is still dark.
I've tried opening 'gconf-editor'/apps/gnome-power-manager/ and setting all applicable settings to 100%.  Still dark.
Any ideas?

---

### Post by laurenbanjo on 2010-11-12
Have you tried using the brightness keys on your computer? I don't know if it's on your aspire model, but on my two models you press Fn and the right arrow to increase brightness.

---

### Post by nsus on 2010-11-12
hi lauren,
I forgot to mention that the brightness hotkeys do not work in ubuntu either.

thanks for the try

---

### Post by laurenbanjo on 2010-11-12
Have you tried using the power settings in Ubuntu Tweak? Here's a screenshot.

---

### Post by nsus on 2010-11-12
I installed 'ubuntu tweak' and reset both ac and battery settings to 100%.  no change in brightness.  even in 'ubuntu tweak' my cursor was slowed down while moving the brightness adjustment bar, but it didn't freeze up completely, as with the panel brightness app.

still no luck, but thanks for the help

---

### Post by quyvuong00 on 2010-11-13
oh , i have the same problem, and i fixed by:

turn on terminal and type :

sudo gedit /etc/default/grub


and then you can Change the line GRUB_CMDLINE_LINUX="" into
Code:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"
then run  sudo update-grub


it worked. i user Acer asprise 4741.
:P

---

### Post by nsus on 2010-11-28
_thank you _[quyvuong00]("http://ubuntuforums.org/member.php?u=1153303").  I've used this fix on both computers I have running 10.10.  perfect fix; rebooted and everything was as it should be.  cam on ong!

---

### Post by adityavpratap on 2010-12-06
> **quyvuong00 said:**
> oh , i have the same problem, and i fixed by:

turn on terminal and type :

sudo gedit /etc/default/grub


and then you can Change the line GRUB_CMDLINE_LINUX="" into
Code:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"
then run  sudo update-grub


it worked. i user Acer asprise 4741.
:P
 
Thanks a lot, it worked on my Aspire 5738z as well! :D

---

### Post by ariksasmita on 2010-12-08
> **quyvuong00 said:**
> oh , i have the same problem, and i fixed by:

turn on terminal and type :

sudo gedit /etc/default/grub


and then you can Change the line GRUB_CMDLINE_LINUX="" into
Code:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"
then run  sudo update-grub


it worked. i user Acer asprise 4741.
:P

could this method implemented in 10.04 too? I'm still using the LTS version till today... I'm too busy to start it all over again installing those many apps i'm using now.. :P

Thanks in advance... :KS

---

### Post by ariksasmita on 2010-12-08
forget my question, already tried it on my 10.04 system, Acer 4741.. It works like a charm... Thanks again, thank you sooo much.... :KS:KS:KS

---

### Post by Felipe Ramos on 2011-09-30
That's not worked on my Acer Aspire 4736z :(

---

### Post by bagofchickens on 2011-11-14
Works with Acer Aspire 5733Z. Thank you!

---

