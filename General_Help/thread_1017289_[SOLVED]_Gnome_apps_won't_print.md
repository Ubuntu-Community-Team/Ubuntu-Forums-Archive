---
title: "[SOLVED] Gnome apps won't print"
date: 2008-12-20
forum: General Help
---

### Post by rbmorse on 2008-12-20
Running Intrepid Ibex 64-bit 

Updated the system today, and after the updates GNOME apps cannot print to my networked HP 2605DN Color Laser Printer.  

Firefox prints fine
The Printer test page from system > administration > Printing > right click on printer prints fine
The printer test page from the CUPS server prints fine

Gedit does not print
Evolution does not print
GnuCash does not print
The printer test page from HPLIP does not print
OpenOffice.Org Word processor does not print

I can access the printer's built-in web interface, and can execute the printer's internal test page in that manner. 

No error messages are displayed. Commanding the print works fine, HPLIP indicates a new job has been sent to the printer, and the status light on the printer's front panel blinks once or twice, then returns to steady green (ready).  HPLIP indicates the print job completed successfully, but not output is produced, nor does the printer look like it's trying to print anything. 

The CUPS log(s) do not show any obvious (to me) errors. 

An HP Photosmart 1215 attached to a USB port works correctly, so I'm not in extremis here, but I am about of ink. It all worked fine yesterday, so any ideas would be appreciated.  I know the kernel updated today, but I'm not sure what else.

---

### Post by SPr on 2008-12-21
Look in the system logs for problems relating to printing.
Did you reboot after the kernel update? Turn it off and on again anyway.
Perhaps the drivers need reinstalling after the update.
Does the HPLIP toolbox show any problems?
Check the connections are secure.
Have you turned the printer off and on again?

---

### Post by rbmorse on 2008-12-21
Thank you for the response.

1. Nothing obvious to me. 
2. Yes. And yes.  No change.
3. Done. No change
4. HPLIP toolbox acts like everything is normal, including the starting job and completed job notifications
5. Done, but note the printer will print directly from CUPS and the system printer conf page. And Firefox. 
6. yes, but note that it works sometimes.  The problem seems confined to GTK-related apps. 

I'm thinking the Avahi update.

I also note I'm seeing the same symptoms on my 32-bit installation, but it also updated itself to the -11 kernel and new version of Avahi before I had a chance to intervene. 

I can print with the LaserJet by booting from the LiveCD, installing the printer , mounting the drive with the document and printing from there, so the hardware seems to fine.  Oh yes...Printing from XP on the same machine works, too.  Which, in and of itsself is a bit strange. 

I also have a MacbookPro which accesses the LAN via wireless and it prints fine, too.

---

### Post by rbmorse on 2008-12-21
While I was composing the previous, I reveived notification of updates available...including CUPS 1.3.9-2ubuntu6.  Installing that and a reboot cures all, although just restarting CUPS probably would have been sufficient.

---

