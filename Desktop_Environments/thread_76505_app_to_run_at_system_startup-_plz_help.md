---
title: "app to run at system startup- plz help"
date: 2005-10-15
forum: Desktop Environments
---

### Post by chloe on 2005-10-15
Hi all,

I'm new to this forum and Ubuntu. 
I have been using linux for about 2 months but last week started using Ubuntu 5.04, a mate told me it’s very good.

I'm having problems with scripts that run my mobinterface at system startup.

I have 2 scripts that run to start the deamons for the mobinterface; 1 starts smsd (/usr/local/bin/smsd_start) and another one start the interface (/usr/local/bin/mobinterface_start). 

My problem is where to put these scripts? I have tried putting them in "/etc/init.d/bootmisc.sh" but the system doesn't start them at boot time.

One of them accesses mysql, apache & php; i guess i need to tell the system to run the script after mysql & apache daemons are started. Problem i don't know how?

The scripts work fine when i manually run them in the terminal.

Any help is highly appreciated.

Thanks for the help in advance.

Regards,

Chloe

---

