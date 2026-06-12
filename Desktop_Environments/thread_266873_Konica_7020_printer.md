---
title: "Konica 7020 printer"
date: 2006-09-27
forum: Desktop Environments
---

### Post by aanderse on 2006-09-27
trying to install a Konica 7020 printer/fax/photocopier all in one but when i try to add a new printer there is no Konica even on the list of printers to add.  has anyone had any experience with this printer, or a printer similar to it?  i'm just looking for advice on how to get this printer working (i've never really used a printer on linux before).

thanks for your time

---

### Post by lagagnon on 2006-09-28
That printer is NOT listed at the [www.linuxprinting.org](www.linuxprinting.org) website, so there is a very good chance you might not be able to get it working under Linux.

You did the research before hand about Linux-printer capatibility before you bought it did you not?

---

### Post by aanderse on 2006-09-30
i never bought the printer.  my brother in law runs an industrial plant and his computer which runs windows crashed for the third time on him.  i offered the suggestion that linux **might** be an alternative to consider.  i showed him ubuntu and went over all the details of switching his computer over to it: he was quite impressed.  the only problem is that he has this printer which is very important.  i'll have to go down to his plant and see if i can come up with a solution for him if he is going to go ahead and switch to linux for a business solution.
i'm quite aware the printer isn't on linuxprinting.org as that was the first place i looked.

any other possible solutions for my brother in laws problem would be greatly appreciated.

---

### Post by Rugger on 2006-12-27
Curious if anybody ever got this figured out.  I've had luck to the point of being able to print to it, but all I get is garbage, hehe.

---

### Post by Rugger on 2006-12-27
Okay, I got it figured out. I use gentoo as my distro but cups should be the same in ubuntu. It's actually quite easy. Just install and configure cups like normal + foomatic. Then go the the webinterace (localhost:631) and add printer and select:

Device: AppSocket/HPJetDirect
Device URI: socket://printerIPaddress:9100
Make: Generic
Model: Generic PCL 6/PCL XL Printer Foomatic/ljet4(en)

After adding the printer you might have to go to configure and select 600 resolution. One computer got that just fine but another had 75 dpi by default.

---

