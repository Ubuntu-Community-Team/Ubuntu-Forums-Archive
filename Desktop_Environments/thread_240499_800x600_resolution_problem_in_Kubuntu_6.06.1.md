---
title: "800x600 resolution problem in Kubuntu 6.06.1"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Peter Mount on 2006-08-20
Hi

I had my screen resolution to the maximum but I wanted to drop to 800x600 to test a web site I'm working on.

When I tried to boot up in 800x600 the screen just became a mess with 2 light coloured horizontal bands (one made of smaller horontal bands and the taskbar some different pattern) and the standard blue "bubbly" desktop just a jumble of small blue horizontal bands.

I have a Pentium 2-350 with an ATI Radeon 7000 64MG PCI video card. 

When I tried this before upgrading from Dapper 6.06 to 6.06.1 it seemed to work fine when I went to 800x600 screen resolution. I've now got KDE 3.4 from the ubuntu repositories

Is there a way for me to fix this? I have a copy of Knoppix so I can boot from that with that hard drive

I hate to ask this but is Ubuntu more stable than Kubuntu in regards to this? I've got Ubuntu loaded on the other hard drive.

Thanks

---

### Post by songo on 2006-08-21
try to increase the refreshement rate, say 75 or 80Hz

---

### Post by Peter Mount on 2006-08-21
How do I do that if I can't get into the GUI?

Thanks

---

### Post by Peter Mount on 2006-08-21
Hi

I managed to fix my problem by using:

sudo dpkg-reconfigure xserver-org

It's now working OK in 800X600 screen resolution at 85Hz

Thanks

---

### Post by der_joachim on 2006-08-21
> **Peter Mount said:**
> 
When I tried to boot up in 800x600 the screen just became a mess with 2 light coloured horizontal bands (one made of smaller horontal bands and the taskbar some different pattern) and the standard blue "bubbly" desktop just a jumble of small blue horizontal bands.


If you test your web site in Firefox: install an extension called Web Developer. Amongst LOTS of other things, it allows you to resize a FF window on the fly. Also: when your X server is configured correctly, Ctrl-Alt-+ and Ctrl-Alt-dash (-) will resize your desktop on the fly.

---

### Post by songo on 2006-08-22
> **der_joachim said:**
> when your X server is configured correctly, Ctrl-Alt-+ and Ctrl-Alt-dash (-) will resize your desktop on the fly.
nice tip! however how can it be usefull?

---

