---
title: "how to get Battery Charge Monitor to work?"
date: 2005-05-19
forum: Desktop Environments
---

### Post by dabear on 2005-05-19
I've successfully installed ubuntu on my new laptop; Toshiba Satelitte L10/cm370-512-6. 
One thing still remains though, and that's to get the battery charge monitor to work properly. It just sits there in my windowlist saying 
"system is running on battery power
Battery status unknown". This happens if I run on battery power or on electric current.

 How do I fix this?

---

### Post by Sniffer on 2005-05-19
[QUOTE=dabear]I've successfully installed ubuntu on my new laptop; Toshiba Satelitte L10/cm370-512-6. 
One thing still remains though, and that's to get the battery charge monitor to work properly. It just sits there in my windowlist saying 
"system is running on battery power
Battery status unknown". This happens if I run on battery power or on electric current.

 How do I fix this?[/QUOTE]


Sorry for the question...but did you try to go the properties of the battery applet??

---

### Post by tread on 2005-05-19
Also, after you bootup, if you booted with the power cable in, remove it and see if the status changes after a bit. If you booted without the power cable, plug it in and see what happens.

---

### Post by dabear on 2005-05-19
[QUOTE=Sniffer]Sorry for the question...but did you try to go the properties of the battery applet??[/QUOTE]Yes, I did go to the preferences if that's what you're talking about. Nothi
ng there helped me. There are no changes at all when I pull out the power cable..

---

### Post by dabear on 2005-05-20
I've now search through google about a million times, and I did find something interresting; because I have a phoenix bios, I don't have support for acpi as a default.   I'd have to patch the kernel or someting..

I'm not that comfortable with linux yet, so I wondered if anbody knows where I can find an already patched ubuntukernel?
I am currently using  2.6.10-5-386

---

### Post by depele on 2006-01-11
same problem, same computer! won't work! 
they told me to recompile my kernel, but it's al little bit to enhaced for me! 
somebody an idea?

---

### Post by navsan_enigma on 2006-01-21
Same problem here : acer laptop. Aspire 5002NWLMi
Turns out I have acpi1.0b . I guess ubuntu only supports acpi2.0 onwards as my friend does not experience the problem with his comp.

---

### Post by Roj on 2007-08-10
I have a similar problem with my Presario 1700 Laptop. When it starts up, it says that there is a "Known ACPI Bios Problem" and then boots into Ubuntu. Everything seems to work fine, except the battery Charge Monitor doesn't show how much battery life is left (just like dabear and depele). I also get an error that says my kernel does not have ACPI support when I run acpi -b.

I looked around and noticed that there isn't a /proc/acpi/ folder on my laptop. I've also found out that the Presario 1700s do not have apm (just acpi). 

Is there anything I can do to find out how much battery life I have, or am I SOL?

---

### Post by saj0577 on 2007-08-17
Same problem, can someone who has recompiled their kernel and knows how to please do a nice step by step process we  need to follow as many people are having this problem. My problem with this occured after the new security updates (about a week ago) before then it worked fine.

So someone please give us a step by step guide on how to recompile my kernel so i have the acpi from the last version (which my battery worked on). Currently the laptopt does not even detect that their is a batter connected it is constantly  "System is running on AC power No battery present." even when i run the laptop of its battery power.

Thanks
Saj

Or if someone could help me on msn that would be great as well and walk me through it.

---

### Post by saj0577 on 2007-08-22
Any updates anyone? Please help us out.

Saj

---

### Post by -Outcast- on 2007-09-03
Has anyone got any further with this?

I posted something similar 2 months ago with nothing. Seems bad at this stage that so many still do not know what their charge is.

---

### Post by christopinka on 2008-07-04
Same problem with Dell Latitude D620.

---

