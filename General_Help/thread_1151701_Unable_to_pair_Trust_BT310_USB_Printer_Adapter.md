---
title: "Unable to pair: Trust BT310 USB Printer Adapter"
date: 2009-05-07
forum: General Help
---

### Post by manolomanolo on 2009-05-07
Hi to all.

I'm trying to connect to my USB printer Adapter. I try to setup a new device using "Bluetooth Applet 1.8" ([www.bluez.com](www.bluez.com)) and the printer adapter is listed between the possible devices.
The device does not require a PIN or a Pass key as shown here:
[http://www.trust.com/products/product.aspx?artnr=14107&cxt=manuals](http://www.trust.com/products/product.aspx?artnr=14107&cxt=manuals)

I don't know how to apply that MS Windows procedure to GNU/Linux.

Actually that applet asks for a pin code but I'm unable to tell it that the adapter does not require one. Also "Automathic PIN code selection" does not work. It sais: Pairing with BlueTooth Printer failed

Any suggestion please?
Thanks

Ubuntu 9.04 on Acer Aspire 5730z

---

### Post by ironbishop on 2009-05-08
Did you try with CLI?

Type 'hcitool scan' to find the address of the device(s) in the bluetooth range. Type 'hidd --connect <bt_addr>' (need root privileges) to connect without PIN. 

In Ubuntu Intrepid Ibex you have to install bluez-compat package to get hidd.

---

### Post by manolomanolo on 2009-05-08
Thanks.

> manolo@manolo-acer:~$ hcitool scan
Scanning ...
	00:0B:0D:10:82:E4	Bluetooth Printer
manolo@manolo-acer:~$ hidd --connect 00:0B:0D:10:82:E4
manolo@manolo-acer:~$ hidd --show
manolo@manolo-acer:~$


Hot to find out whether I've been able to connect to the printer adapter or not? As you can see the command 'hidd --show' gave no results.

Then, how to discover my printer?

---

### Post by ironbishop on 2009-05-08
LOL ma perché stiamo scrivendo in inglese? :)
 
The printer itself should give you a feedback when a connection is established. I don't know if Ubuntu has automatic bt printer discovery! For example: udev does the discovery job for USB device, and so on.

---

### Post by manolomanolo on 2009-05-08
> **ironbishop said:**
> LOL ma perché stiamo scrivendo in inglese? :)
[I](Perchè questo è un forum in lingua inglese ed è letto da persone che probabilmente non conoscono altre lingue)
[/I] 

> The printer itself should give you a feedback when a connection is established. I don't know if Ubuntu has automatic bt printer discovery! For example: udev does the discovery job for USB device, and so on.

My printer is a DCP-145c.
[http://welcome.solutions.brother.com/BSC/public/eu/it/it/model_top/colormfc/dcp145c_eu_as.html?reg=eu&c=it&lang=it&prod=dcp145c_eu_as](http://welcome.solutions.brother.com/BSC/public/eu/it/it/model_top/colormfc/dcp145c_eu_as.html?reg=eu&c=it&lang=it&prod=dcp145c_eu_as)

I downloaded and installed the drivers from Brother web site:
[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

The scanner and the printer work perfectly so we could exclude there could be any printer/scanner problem.

Ubuntu has an automatic printer discovery system but the problem is I'm still unable to connect to my BT printer adaptor!

---

### Post by manolomanolo on 2009-05-13
Still no suggestions?

---

