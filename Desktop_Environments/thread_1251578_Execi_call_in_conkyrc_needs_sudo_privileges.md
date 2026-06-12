---
title: "Execi call in conkyrc needs sudo privileges"
date: 2009-08-27
forum: Desktop Environments
---

### Post by tgeer43 on 2009-08-27
Actually an execi call in my conkyrc is calling a script in my home directory which in turn calls hddtemp. Hddtemp needs sudo privileges.

Here's the execi call in .conkyrc:
```
${execi 30 ~/Scripts/hddtemp.sh}
```And here's the hddtemp call in my script:
```
hddtemp SATA:/dev/sda SATA:/dev/sdb > /tmp/hddtemp-info
```Just to test the script I've been prefixing the call with gksudo but naturally I don't want my conky prompting me for permission.

Is there a way to make it run without interaction?

And yes, I know that conky has an hddtemp variable built-in but I wanted my temperatures in Farenheit and formatted in a certain way.
My script handles this nicely.

Thanks in advance,

tgeer

---

### Post by tgeer43 on 2009-08-27
There I go answering my own questions again. :wink:

I ran: 'dpkg-reconfigure hddtemp' and was prompted to set the SUID bit, allowing regular users to call it without a password.

Yeah, I know I could use 'chmod' to do the same but to be honest, I never think about those darn sticky bits. If 'dpkg-reconfigure' had not prompted me about it, I'd probably still be scratching my head.

Hopefully this will help someone else with a similar situation.

tgeer

---

