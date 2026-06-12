---
title: "printing issues on ubuntu jaunty"
date: 2009-04-24
forum: General Help
---

### Post by dagarshali on 2009-04-24
Hi,
I have ubuntu jaunty installed.. I have a canon pixma ip1700 printer, which i installed using ip2200 driver. the instructions for using that were found else where on the web..

I then went to localhost:631 and i was able to print the testprint without any issues.. But it stops right there..i can't print any other stuff from firefox.. neither can i print from openoffice or gedit.

However, i am able to print i go to the console and use lpr command.

i have already asked this question a few days ago..but haven't gotten any response.. 

i would really appreciate if you could tell me what to do/look for.

Thanks a lot

vishwa

---

### Post by tbm on 2009-04-27
I also have a print problem, don't know if its related though.
I try to print on a network printer (Lexmark-X560n), but it always prints on Letter format, regardless of setting printer properties to A4. Same happens also after reboot, and properties on printer is ok (A4). I have not Letter format in bin, thus fails. Quite annoying. Any help much appreciated...

Cheers,
Tom

---

### Post by tbm on 2009-04-27
Ahhh. Looks like there is "something" that 'system-config-printer' and/or 'http://localhost:631' does not change:

Edit file: /etc/papersize
Change 'letter' to 'A4'.

Now it works!
This must be a bug?

T

---

