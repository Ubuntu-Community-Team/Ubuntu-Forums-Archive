---
title: "Setting Up Custom Port for Evolution EMail"
date: 2008-12-25
forum: General Help
---

### Post by Billsey on 2008-12-25
I need to know how to set up an email account to send mail (SMTP) using a non-standard port to contact the target server. I can't find anything in the documentation, or online, but I'm sure there **must** be a way to do this.

The account's client is on my laptop and the server is my own domain (the hosting company allows the use of a non-standard port, which they have already configured on their servers so that customers can send mail directly through their servers even if the customer's normal ISP doesn't want to allow them to get to another company's SMTP servers). The reason I have this problem is that if I'm not home on my own network, I'm not using my normal ISP&#8212;and my normal ISP doesn't seem to want to let me use their SMTP servers unless I'm doing it from home.

Thus I need a setup that I don't need to change every time I use the laptop in a different location. I **think** that the non-standard port will solve this, but I need to know how to configure Evolution to use that port for that account for it to work.

Please help.

---

### Post by plucky on 2008-12-25
> I need to know how to set up an email account to send mail (SMTP) using a non-standard port to contact the target server. I can't find anything in the documentation, or online, but I'm sure there must be a way to do this.


When you are setting up your smtp server name i.e **smtp.isp.com** you have to enter the port you want it to use after the address i.e **smtp.isp.com:995** will tell evolution to use port **995**.

Also the same for incoming pop or imap addresses i.e pop.isp.com:65


Good Luck

---

### Post by Billsey on 2008-12-25
> **plucky said:**
> When you are setting up your smtp server name i.e **smtp.isp.com** you have to enter the port you want it to use after the address i.e **smtp.isp.com:995** will tell evolution to use port **995**.

Also the same for incoming pop or imap addresses i.e pop.isp.com:65


Good Luck

So far, so good. :-D

Next test will be when I'm **not** at home. ;-)

I did examine the headers to see what the path was, and it checks out.

By the way, this **was** a major D'uh. Thanks for the help. :-)

**UPDATE:** All tests passed. Yippee! :-D

---

