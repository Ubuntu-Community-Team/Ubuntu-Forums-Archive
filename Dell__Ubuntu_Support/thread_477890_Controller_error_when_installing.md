---
title: "Controller error when installing"
date: 2007-06-18
forum: Dell  Ubuntu Support
---

### Post by mikessilo on 2007-06-18
Trying to install ubuntu on a poweredge 6450 blade server and getting the error i2o : iop0 : could not activate controller.  the raid controller is pci scsi and the configuration is raid 5 with 4 drives.
tried switching controller ports and that didn't work and the bios seem to be up to date.
dont know what to do

---

### Post by angryfirelord on 2007-06-20
No idea if this will work, but open up a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```
Scroll down until you see the 1st Ubuntu entry (title Ubuntu blah blah blah). On the kernel entry, add **acpi=no** to it with everything else on that line.

---

### Post by eRgal on 2007-06-25
I just came accross exactly the same issue, I have a dell perc controller and was able to fix this by going into the scsi controller bios/option (control M at startup) in the options I change the mode of the card from i20 mode to mass storage and this seemed to work no problem.

I am not sure if you have the same card/options in the bios of scsi card but just thought this may help someone.

Cheers.

---

### Post by rv2221 on 2007-08-04
On my Dell PowerEdge 4400 PERC 2/DC controller I had the very same problem and this fix worked for me too.  
CTRL-M on boot up>Objects>Adapter>change "I20" to "MASS STORAGE">Reboot>everything working :-)
rv2221

---

### Post by dherring on 2007-10-23
FIXED!

I was in the process of upgrading a DELL PowerEdge 1300 with a PERC 2/SC RAID controller card from Windows to RHEL 5, and I was experiencing the dreaded "i2o: iop0: could not activate controller" error.

I tried several of the boot options that were suggested (like acpi=no and pci=noacpi), but none worked. I saw the solution that worked for some people that involved doing Ctrl-M during the boot process and going into the PERC 2 BIOS and changing the card from I20 mode to MASS STORAGE mode, but my version of the PERC 2 BIOS administration program did not offer that option.

My solution was to update the old PERC 2/SC BIOS (2.10/v1.26) to the latest version available from the DELL support website (3.00/v1.36). 
I was then able to Ctrl-M into the controller BIOS at boot time and see the Objects->Adapter->Emulation setting, which I changed from i20 to MASS STORAGE. The system booted normally!

As a side note, none of my windows machines have floppy drives anymore, so here is a simple procedure I developed to create a bootable BIOS update CD from DELL's .EXE BIOS updates that require a floppy:

1. Create a virtual floppy drive.

- Download and install Virtual Floppy Drive (VFD -- Google it).
- Start VFDWIN.EXE from the installation directory.
- Click the Install button to install the VFD driver.
- Click the Start button to start the VFD driver.
- Click the Change button and change the drive letter from (NONE) to A (or any other available drive letter on your system).
- Click the Open button and create a new image file (Disk Type=RAM, Media Type=3.5” 1.44MB, write-protect unchecked).
- Verify that the virtual floppy drive is working and accessible using File Explorer.

2. Run the BIOS update .EXE, choosing the virtual floppy drive as the destination. Use File Explorer to verify the files were successfully extracted.

3. Use Magic ISO Maker to create a bootable CD image containing the BIOS update files.

- Download and install MagicISO (Google it).
- Start MagicISO.
- Click “Load Boot Image” and choose “From bootable floppy driver”.
- The indicator in the main window should now read “Bootable”.
- Drag and drop the files and directories from the virtual A: drive window into the MagicISO file window (the upper right-hand corner window).
- Put a blank CD into the CD burner drive.
- Click on “Burn the current image without saving”.
- Choose the burner drive, select a write speed and click Burn It!
- The BIOS update CD is ready to install.
- Save the image on your hard drive, if you wish, for future reference.

4. Terminate the virtual floppy drive.

- In the VFD console, click Close. (Saving the updated image file is optional.)
- Close the VFD console application.

5. Install the BIOS update using your shiny new BIOS update CD.

---

