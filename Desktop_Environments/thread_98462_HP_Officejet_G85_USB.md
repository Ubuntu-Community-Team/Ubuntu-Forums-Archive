---
title: "HP Officejet G85 USB"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Avenolpey on 2005-12-03
I just installed Breezy Badger and both my printers were recognized.  I have no problem printing to my Laserjet 4050 but when I print to the officejet the jobs go in but no printing.  I then used the option to find other devices and the system saw the USB port and recognized the printer.  Still no printing.  Any ideas?

thanks in advance

---

### Post by stevec on 2005-12-03
I also have a G85 that doesn`t work. It did though,until about 3 weeks,then it just stopped. Same problem as you,the printer is recognised and appears to install properly but print jobs just sit in the queue.I have since tried many things including,uninstalling then reinstalling all print related packages but to no avail.I`ve also tried it on other distributions,but on all of them I get the same result.To make sure my printer still worked I even rebuilt an old pc and installed windows on to it.On windows the printer worked perfectly.
I also have a deskjet 3940 which works no problem, so like you I can still print but the G85 is very frustrating at the moment.
          Good luck

---

### Post by antidrugue on 2005-12-03
I have an HP Deskject 842c, that's how I did it:

Install the required package:
```
        
sudo apt-get install printconf

```

Restart the print server:
```

sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

```

Now open a browser and go at [http://localhost:631](http://localhost:631)
                > Click "Printers"
                > "Add printers"
                > Enter Name, Location, Description ; then click "Continue"
                > From the Device drop-down list, click hp:/usb/[printer name, serial number].
                        For example, "hp:/usb/hp_deskjet_842c?serial=MY31R1K02179".
                > Click "Continue"
                > In the "Make" list, click "HP", and then click "Continue"
                > In the "Model" list, click the printer model, and then click "Continue"
                        (you should choose the foomatic recommended driver specific to your printer)

That's it, works for me.

---

### Post by Hairy_Palms on 2005-12-03
to get my officejet to work i simply had to install the hpoj package from synaptic, then i can print and scan to my hearts delight.

---

### Post by uboltun on 2006-10-03
hpoj worked for my G85xi, but "/etc/init.d/hpoj setup" couldn't detect the printer until I turned it off and then on again.

---

