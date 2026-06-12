---
title: "Expert needed"
date: 2008-02-04
forum: Desktop Environments
---

### Post by canadianbaptist on 2008-02-04
I have had a problem with my power icon always showing that I am on A/C even when on battery.. this all started when I disabled something in services (I am new to this, my fault I know). I have posted about this with no answers.

Now I have found a clue that maybe someone can diagnose. I downloaded boot up manager and I see when I shutdown hal, my power icon cannot get data. When I restart it it reads the power properly until I reboot.

Somehow hal is not continuously reading the power status. Does this tell anybody anything about the solution.... :confused:

---

### Post by Tenken on 2008-02-04
What services did you disable? Your battery generally get it info from the acpi daemon (acoid), unless it's a really old latop.

EDIT: acpid, not acoid

---

### Post by canadianbaptist on 2008-02-04
> **Tenken said:**
> What services did you disable? Your battery generally get it info from the acpi daemon (acoid), unless it's a really old latop.

I cannot remember.... I am an idiot I know :) My laptop is newer... i will poke around "acoid"

---

### Post by canadianbaptist on 2008-02-04
> **Tenken said:**
> What services did you disable? Your battery generally get it info from the acpi daemon (acoid), unless it's a really old latop.

EDIT: acpid, not acoid

OK, I poked around the processes and when I change "Hal" to "99" priority (I assume this is last) I get it to work BUT start up took about 3 min????

Any ideas?

---

### Post by Tenken on 2008-02-04
Make your the "Power Managment" services are running under System->Administration->Services

---

