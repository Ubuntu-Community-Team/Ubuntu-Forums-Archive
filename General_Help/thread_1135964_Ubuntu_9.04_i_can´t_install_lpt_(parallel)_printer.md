---
title: "Ubuntu 9.04 i can´t install lpt (parallel) printer"
date: 2009-04-24
forum: General Help
---

### Post by pancho2500 on 2009-04-24
Hi, i just made a fresh install from ubuntu 8.10 to 9.04 and now i can´t install my parallel port printer. i can´t select printer from lpt (parallel) port, beacause i can´t see this option. i need the printer it´s an epson stylus color 400, i use it to work!!! What can i do?
I allways use the alternate version beacause i use the ltsp server with thin clients.

In version 8.10, i installed it without a problem.

Thank you very much

Pd: I search in dev directory and there isn´t lp0

---

### Post by pancho2500 on 2009-04-24
please i need this very urgent, i dont wanna reinstall 8.10 for this. 

Thanks for the patience

---

### Post by cariboo on 2009-04-24
Have you got the paraport driver loaded? To check open a terminal and type:

```
lsmod | grep para
```

if the module is installed you should see something like this.

```
lsmod | grep para*
parport                49584  2 ppdev,lp
```

---

### Post by pancho2500 on 2009-04-24
> **cariboo907 said:**
> Have you got the paraport driver loaded? To check open a terminal and type:

```
lsmod | grep para
```

if the module is installed you should see something like this.

```
lsmod | grep para*
parport                49584  2 ppdev,lp
```

hi thanks for your answer, i do 
```
lsmod | grep para
```
and i see nothing
i see this 
```
 francisco@ubuntu:~$ lsmod | grep para
francisco@ubuntu:~$ 
```
what can i do? it seems 9.04 doesn't come with lpt support?

if i put the * i see this

```
 francisco@ubuntu:~$ lsmod | grep para*
parport                42220  2 ppdev,lp
```

---

### Post by pancho2500 on 2009-04-24
if someone tell me where is the parallel port location file, maybe i can put this in the printer wizard port in other: URI of the device. beacause there isn´t any more lpt option:(

---

### Post by cariboo on 2009-04-24
I'm running Jaunty, and the paraport module is loaded by default. To load the paraport module. open an Applications-->Accessories-->Terminal and type:

```
sudo modprobe paraport
```

this will load the paraport module, and you should see it in System-->Administration-->Printing

---

### Post by pancho2500 on 2009-04-24
> **cariboo907 said:**
> I'm running Jaunty, and the paraport module is loaded by default. To load the paraport module. open an Applications-->Accessories-->Terminal and type:

```
sudo modprobe paraport
```

this will load the paraport module, and you should see it in System-->Administration-->Printing

i do that but with paraport tells me that the module not found but with parport doesn't return the error.
When i go to system administration printing  new printer
only are serial port1 serial port 2 other and lan but there isn't any lpt option. What am i doing wrong?

---

### Post by cariboo on 2009-04-24
I found a howto [here]("http://newbiedoc.berlios.de/wiki/Setting_up_a_parallel_printer_using_CUPS") using cups to setup your printer. I used this method to setup an HP laser printer on my server. To access the cups interface open firefox and type in the address bar:

```
http://localhost:631
```

---

### Post by pancho2500 on 2009-04-24
> **cariboo907 said:**
> I found a howto [here]("http://newbiedoc.berlios.de/wiki/Setting_up_a_parallel_printer_using_CUPS") using cups to setup your printer. I used this method to setup an HP laser printer on my server. To access the cups interface open firefox and type in the address bar:

```
http://localhost:631
```

there in cups it´s the same are all ports less the lpt, in your 9.04 you can see the lpt option?

---

### Post by cariboo on 2009-04-24
OK lets try something different.

Make sure that the printer is connected to your system and powered on.
#

Open a terminal/console and check if the lp and ppdev kernel modules are loaded:
$ lsmod | grep lp
$ lsmod | grep ppdev
#

Check if the kernel detected the parallel port during bootup:
$ dmesg | grep par 
#

Find out if your printer gets detected by CUPS:
$ lpinfo -v

Let me know the results

---

### Post by pancho2500 on 2009-04-24
> **cariboo907 said:**
> OK lets try something different.

Make sure that the printer is connected to your system and powered on.
#

Open a terminal/console and check if the lp and ppdev kernel modules are loaded:
$ lsmod | grep lp
$ lsmod | grep ppdev
#

Check if the kernel detected the parallel port during bootup:
$ dmesg | grep par 
#

Find out if your printer gets detected by CUPS:
$ lpinfo -v

Let me know the results

here you got
```
francisco@ubuntu:~$ lsmod | grep lp
lp                     17156  0 
parport                42220  2 ppdev,lp
francisco@ubuntu:~$ lsmod | grep ppdev
ppdev                  15620  0 
parport                42220  2 ppdev,lp
francisco@ubuntu:~$ dmesg | grep par 
[    0.296911] Booting paravirtualized kernel on bare hardware
[    3.273285] PM: Resume from partition 8:5
[   20.559441] ppdev: user-space parallel port driver
francisco@ubuntu:~$ lpinfo -v
network socket
network beh
direct hal
direct hpfax
direct hp
network http
network ipp
network lpd
direct scsi
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
network smb
francisco@ubuntu:~$ 
```

---

### Post by cariboo on 2009-04-24
This may be a dumb question, but is the printer connected and turned on?

Everything seems to be working the way it should, except for detecting the printer.

---

### Post by pancho2500 on 2009-04-25
> **cariboo907 said:**
> This may be a dumb question, but is the printer connected and turned on?

Everything seems to be working the way it should, except for detecting the printer.

yes it´s conencted and powered on

---

### Post by cariboo on 2009-04-25
I'm stumped, the only other thing I can suggest is to reboot the system and see if the printer is detected

---

### Post by pancho2500 on 2009-04-25
> **cariboo907 said:**
> I'm stumped, the only other thing I can suggest is to reboot the system and see if the printer is detected

i reboot but the problem persists, y rebooted with the 8.10 live cd and the printer works well, the problem es with 9.04.

Thanks, i keep searching

---

### Post by pancho2500 on 2009-04-25
> **cariboo907 said:**
> This may be a dumb question, but is the printer connected and turned on?

Everything seems to be working the way it should, except for detecting the printer.

it seem you was right, i reset bios and change a couple of things there and works!!!! testing now...

---

### Post by Gamer_2k4 on 2009-04-25
> **pancho2500 said:**
> it seem you was right, i reset bios and change a couple of things there and works!!!! testing now...
Could you elaborate on that just a bit? I'm having the same problem with my computer; the parallel port never shows up as an option when I'm trying to install printers, and the printer that was working with 8.10 now gives a "not connected" error since I've upgraded to 9.04.

This is the only printer I have, and I'd like to be able to print again.  What exactly did you change to make it recognize parallel ports again?

---

### Post by collins_ on 2009-04-26
Same problem with me.
lsmod finds eveything... But I don't have the opportunity to see lpt with lpinfo -v ...
Of course this printer works fine with another system : an old debian edgy on the same computer!
A problem with kubuntu 9.04 ?????

---

### Post by FrancisT on 2009-05-05
> **Gamer_2k4 said:**
> Could you elaborate on that just a bit? I'm having the same problem with my computer; the parallel port never shows up as an option when I'm trying to install printers, and the printer that was working with 8.10 now gives a "not connected" error since I've upgraded to 9.04.

This is the only printer I have, and I'd like to be able to print again.  What exactly did you change to make it recognize parallel ports again?

"Reset the Bios" appears to mean following the instructions here:
[http://newbiedoc.berlios.de/wiki/Setting_up_a_parallel_printer_using_CUPS#BIOS_setting_for_parallel_port]("http://newbiedoc.berlios.de/wiki/Setting_up_a_parallel_printer_using_CUPS#BIOS_setting_for_parallel_port")

This doesn't work for me however and I have raised bug [372296]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/372296") (which is now listed as a duplicate of bug [369850]("https://bugs.launchpad.net/bugs/369850")

---

### Post by Gaping Goatse on 2009-05-06
I have found a fix.

Im running Ubuntu 9.04 Desktop on an old machine. I have a HP Laserjet 4 via /dev/lp0

I lsmod'ed to make sure the appropriate modules were loaded. I then checked dmesg to see what was in there. And lpstat still showed no /dev/lp0 activity. My experience thus far mirrors everybody else.

The fix:

josh@comp1:~$ sudo modprobe parport_pc

After you type in your system passwd, you should see a line either on stdout or dmesg along the lines of

parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]

After you modprobe the appropriate driver, /dev/lp0 will work and CUPS will alert you of a printer on that parallel port. To keep this working across reboots, add parport_pc to /etc/modules . It now should just work.

---

### Post by cariboo on 2009-05-06
For those of you looking in the bios for a solution, there is a paralllel port setting, on the computer I checked i have:

[list]
[*]SPP
[*]EPP
[*]ECP
[*]ECP+EPP
[/list]

I would suggest trying the ECP+EPP setting, it might solve the problem.

---

### Post by petersk on 2009-05-09
Gaping Goatse,

 Your modprobe solution seems to be working for me.  Is that something they left out because they thought no one used parallel printers any more?

---

### Post by iamkrazee on 2009-09-12
Funny.. I just installed a couple of packages from synaptic, after searching for the keyword "parallel printer" and now it seems to be working perfectly for me. 

Actually, ubuntu's taking it's ultra slow test-print, got bored and searched if such thread exists :P :popcorn:

---

### Post by dziprick on 2009-11-14
Same problem here.  Upgraded to 9.04 and could not see the LPT printer option.  Followed advice above where I went to the package manager, searched for 'parallel printer' and installed a bunch of the options that looked relevant.  Then when I went to 'add new printer', not only did the parallel port show up, my printer was recognized and I just had to click on my printer.  All worked fine then.

:)

---

