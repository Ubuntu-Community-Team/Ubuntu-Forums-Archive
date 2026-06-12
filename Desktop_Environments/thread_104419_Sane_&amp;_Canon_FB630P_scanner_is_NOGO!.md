---
title: "Sane &amp; Canon FB630P scanner is NOGO!"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Ranime on 2005-12-16
HI there,

I have a paralel flatbed-scanner by Canon (FB630P) and it isn't recognised by sane. This is what I get when I do a sane-find-scanner:
```
ranime@ishtar:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a driver for your USB host controller and have installed a
  # kernel scanner module.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
ranime@ishtar:~$

```

The scanner **is** supported by sane as is stated here: [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

Can someone tell me what I'm doing wrong?

---

### Post by trollzor on 2006-03-26
Hey Ranime,

a guy claiming to have it fixed
[http://ubuntuforums.org/showthread.php?t=91879&highlight=canon+scanner](http://ubuntuforums.org/showthread.php?t=91879&highlight=canon+scanner)

or, my method:

get the source from these guys
[http://canon-fb330p.sourceforge.net/](http://canon-fb330p.sourceforge.net/)

search synaptic for "libieee1284" and get it

make sure you have "build-essential" too for compiling

untar the source into a directory
./configure
make
sudo make install

then when you use it


sudo modprobe parport_pc
sudo ./scan -C       #this configures it, only need to do it once
sudo ./scan -3 -c -r 600 -S 5104,7016 -o scan.tga

This last command sets it to type 3 (our scanner), colour scanning, at a resolution of 600, with the size set to 5000 by 5000 pixels (play around with these numbers), and sets the output to a file called "scan.tga". You can get a list of options by just typing "./scan" on its own.

Then open scan.tga in the Gimp and crop/rotate and save as .png/.jpg/.whatever.

It's slow at 600dpi, but 75 dpi produces readable text and is fast, for some reason it uses 100% cpu, and sometimes it errors out, but most of the time you can get nice quality scans.

---

### Post by vratnica on 2007-04-30
i compiled this driver with libieee, but all I get when running:

[HTML]sudo ./scan -C #
[/HTML]

is:

[HTML]Canon CanoScan(tm) Scanner Driver 6.00. Copyright (C) 2001 Simon Krix et al.
This driver comes with ABSOLUTELY NO WARRANTY; for details
please see http://www.gnu.org/copyleft/gpl.html
This is free software, and you are welcome to redistribute
it under certain conditions.
See the GNU General Public License for details.

Finding IEEE1284 ports...
    parport0 (0x378): <raw><cpt><nbl><byt><swe>... OK (ecp-swe).

Detecting scanner:
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Reply 2 (0x0c in 0x1f) - Status = 0x1f   
initialise: could not wake scanner
Fatal: Unable to initialise scanner! (Code 1)  [/HTML]

i have read somewhere that I should change BIOS settings of paralel port to EPP, i have done it also, but nothing changed

anyone can help?

please...

---

