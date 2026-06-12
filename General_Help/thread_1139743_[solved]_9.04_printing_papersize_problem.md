---
title: "[solved] 9.04 printing papersize problem"
date: 2009-04-27
forum: General Help
---

### Post by tbm on 2009-04-27
I changed network printer Lexmark properties from Letter -> A4.
Print fails; error msg in printer display: Letter format not available, print queue stopped, red led, error beeps...

Looks like there is "something" that 'system-config-printer' and/or 'http://localhost:631' does not change regarding papersize A4:

Edit file: /etc/papersize
Change 'letter' to 'A4'.

Now it works!
This must be a bug?

Cheers,
Tom :-)

---

### Post by vegancorr on 2009-04-28
THANK YOU :D

I updated to 9.04 and today surprise, surprise.. I thought it must have been an issue of paper size, but the printer settings were ok. I didn't know there was an /etc/papersize.. After I kept trying for about one hour for different printer / driver settings, I had to boot in Windows since I was in a big hurry :)

I've just looked for this bug, in a few hours it should be fixed:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/357732)

---

