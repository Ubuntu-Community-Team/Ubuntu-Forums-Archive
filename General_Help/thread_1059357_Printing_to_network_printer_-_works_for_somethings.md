---
title: "Printing to network printer - works for somethings and not others"
date: 2009-02-03
forum: General Help
---

### Post by stormthirst on 2009-02-03
I've been making the effort to switch from Windows to Ubuntu. Most things seem to be working and it's very helpful that I can dual boot my machine.

Most things work out of the box, but I am having trouble getting the printing to work. I have an old HP Laserjet 5MP, connected to a HP jet direct box on the LAN. This works just fine under Windows, so I know it's not a problem with the printer as such.

I added a printer from System -> Administration -> Printing -> New -> HP Jetdirect. I entered the hostname, and then find the right driver supplied with Ubuntu. It then prints a test page just fine. I can print from gEdit just fine. But I can't print from Openoffice Word Processor. I even tried saving the OO document as a PDF, but that won't print either. The printer lights flash for a moment, but nothing else happens. It's almost as if the printer were accepting data, but then rejects it.

Am I missing a trick here? I need to go back and check over the CUPS logs, but I didn't see anything that seemed relevant last time.

Are there any other suggestions about trying to troubleshoot this problem?

Andrew

---

### Post by dcstar on 2009-02-03
> **stormthirst said:**
> I've been making the effort to switch from Windows to Ubuntu. Most things seem to be working and it's very helpful that I can dual boot my machine.

Most things work out of the box, but I am having trouble getting the printing to work. I have an old HP Laserjet 5MP, connected to a HP jet direct box on the LAN. This works just fine under Windows, so I know it's not a problem with the printer as such.

I added a printer from System -> Administration -> Printing -> New -> HP Jetdirect. I entered the hostname, and then find the right driver supplied with Ubuntu. It then prints a test page just fine. I can print from gEdit just fine. But I can't print from Openoffice Word Processor. I even tried saving the OO document as a PDF, but that won't print either. The printer lights flash for a moment, but nothing else happens. It's almost as if the printer were accepting data, but then rejects it.

Am I missing a trick here? I need to go back and check over the CUPS logs, but I didn't see anything that seemed relevant last time.

Are there any other suggestions about trying to troubleshoot this problem?


Chances are small print jobs are getting through, but larger ones may not be - you may be able to confirm this.

In any case you might try manually selecting another print driver, if it is an old printer it may need an old PJL driver (you aren't using Postscript, are you?).

---

### Post by stormthirst on 2009-02-03
> **dcstar said:**
> Chances are small print jobs are getting through, but larger ones may not be - you may be able to confirm this.

In any case you might try manually selecting another print driver, if it is an old printer it may need an old PJL driver (you aren't using Postscript, are you?).

As it happens - yes I am using the POstscript printer driver because that's what was recommended by Ubuntu. I'll try a different driver.

A

---

