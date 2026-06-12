---
title: "Inspiron 4150 &amp; pcmcia dialup ibm modem"
date: 2007-10-29
forum: Dell  Ubuntu Support
---

### Post by jkohler2 on 2007-10-29
This 56k pcmcia modem worked perfectly 1 hour ago on the Inspiron 4150 under Fedora 3 (using the kernel driver pcmcia-cs) Sadly, it didn't work on Fedora 4, 5, 6, or 7 (possibly the new driver pcmcia-utils).

On Ubuntu Feisty Fawn, the Administration-Network-config worked for eth0, but not ppp0.  I tried using all 4 ports--ttyS0, ttyS1, ttyS2, and ttyS3 all to no avail. (under fedora 3, ttyS3 worked)  

Under fedora 3 there was a program "Kudzu" which recognized the pcmcia modem as "generic" and asked to keep generic software.  It worked.

Nothing I've done on Ubuntu could get a dial tone, dialing, and a dialup connection.  

Could it be software?  The Dell  laptop, and IBM pcmcia 56k modem worked with the old Fedora.

---

### Post by dacap06 on 2007-10-31
Oh, how I hate dealing with PCMCIA/Cardbus issues!  But I have done it successfully before, so perhaps my experience can help.  The good news is that PCMCIA support is turned on by default in Ubuntu (unlike older Red-hat based distributions).

The first question I have is whether ANY pcmcia card works?  Do you have a wireless network card, for instance?  This is important because you need two levels of driver.  The first level deals with the PCMCIA holder.  The next level deals with the card itself.  

The lower level PCMCIA holder driver is known as the cardbus manager and responds to Cardbus/PCMCIA insertions and removals.  My purpose for asking is to ensure that the cardbus manager is actually working.  Alternatively, do this:

1 -- ensure that the pmciautils package is installed.  This is the package that contains the two common Linux cardbus managers.  This package replaced the old cardbus_cs software back around kernel 6.13.

2 -- try the lspcmcia command as root in a console window while your modem is in the PCMCIA slot.  It should  show something like:
 Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.0)
  CardBus card -- see "lspci" for more information

3 -- try the lspci command as root in a console and grep for Cardbus (note the capical C).  You should see some line listing your hardware similar to:
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)

4 -- if you see your cardbus bridge, then you can try using the pccardctl command (works better as root) to see how well your card has interfaced with your PCMCIA system.

 ------  "pccardctl status" should show the card as being inserted in the socket

------  "pccardctl info" may or may not show anything useful about the card.

If you aren't getting anything from the above, let's make sure that your system is paying attention to cardbus.  Look at /etc/discover.conf.  It should enable scanning of the cardbus.  The first few lines should look something like this:

# /etc/discover.conf: hardware detection settings
#
# Default settings:
#
# Enable the PCI, USB, IDE, and SCSI bus scans:
enable pci,usb,ide,scsi
#
# Enable the PCMCIA scan too:
enable pcmcia

If you had to change it to enable pcmcia scanning, reboot at this point and redo the steps above.  Further down in that file is scanning of serial and parallel ports.  Scanning these can cause problems, so it normally isn't done.  However, if you are still having problems, turning it on may be worth a try.

Once you get good information from the above, then you need to start working on the driver for the card itself.  Is the IBM PCMCIA modem a full hardware modem or a software modem?  Since it worked with Fedora 3, I am presuming it is a hardware modem.  If so, you'll just need to figure out how to configure it since Linux does a pretty good job of supporting serial ports.  Here you are on your own since I don't have that particular card, nor do I have experience with it.

Good luck!

---

### Post by jkohler2 on 2007-11-23
Thanks for the great suggestions!  Unfortunately I forgot to mention that I am command line challenged, and pretty much limited to clicking the options in a pull-down menu, like system, administration, and network on the desktop.  I guess I'll try another tactic, such as a USB modem in the laptop with the Network dialup configuration.

John

---

