---
title: "Swscanner crashes while scanning channels"
date: 2009-02-10
forum: General Help
---

### Post by hal8000 on 2009-02-10
Using Ubuntu Hardy 8.04 on a HP Compaq nc6400 Laptop.

Labtop has builtin wireless Intel3945ABG chipset and using iwl3945 driver and firmware with Hard 2.6.24-33-generic kernel.

Wifi is recognised as wlan0 and when I start swscanner with this interface and scan, it scans for a few seconds and then stops with message:
"Failed to read scan data"

Any idea how to fix this?

Starting swscanner from terminal gives some possible useful output:

--snip--
if(wlan0)->0.0.0.0/12.0.0.0/96.49.161.182####	level: -256  noise: -256 (0)
if(wlan0)->0.0.0.0/8.234.147.191/2.0.0.0####	level: -256  noise: -256 (0)
wlan0     Failed to read scan data : Resource temporarily unavailable

Scan finished!!
Creating SWSconfig...
New 'scan error' event received...
if(wlan0)->0.0.0.0/96.49.161.182/156.116.159.182####	level: -256  noise: -256 (0)
if(wlan0)->0.0.0.0/96.49.161.182/156.116.159.182####	level: -256  noise: -256 (0)
--snip--

In the text "failed to read scan data" coincides with the message on swscanner, swscanner halts but looks as though the program may be running without X as scanning continues in terminal


Thanks in advance

---

### Post by toddwbucy on 2009-03-03
I am having the exact same problem with this particular wifi card.  However I am using Ubuntu 8.10.  were you able to solve this as I have not been able to find many answers.

Thanks 
Todd

---

### Post by .JNK on 2009-07-11
im having the same problem, swscanner crashes while scanning channels. starting swscanner from the shell (gksudo swscanner) produces some output on the shell. whenever i start scanning channels i get the following error on the shell 
KCrash: Application 'swscanner' crashing... 
and the window closes

im using ubuntu 9.04 on an asus business laptop

---

