---
title: "Brother MFC-440CN Printer help."
date: 2009-02-28
forum: General Help
---

### Post by SVEN1 on 2009-02-28
Well, since my Lexmark x5150 doesn't work with Ubuntu 8.10, went out hunting for a Ubuntu friendly printer.

I picked up a brother MFC-440CN printer almost like new.

Since I am a newbie and don't want to screw things up, can anyone give me step by step directions getting drivers and installing them.

Thanks.

---

### Post by sigurnjak on 2009-02-28
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-440CN](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-440CN)

Here are drivers for you . Download deb files, double click them to install . 
Go to your admin - printing  and set up your printer . It worked for my hl 2140 from brother just fine .

---

### Post by HermanAB on 2009-02-28
For that Lexmark, find an old PC, put WinExPee on it and leave it to lurk in a dark corner as a print server.

Cheers,

Herman

---

### Post by SVEN1 on 2009-03-01
> **sigurnjak said:**
> [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-440CN](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-440CN)

Here are drivers for you . Download deb files, double click them to install . 
Go to your admin - printing  and set up your printer . It worked for my hl 2140 from brother just fine .

Ok it's installed, I can send a print job to que and it goes to processing, nothing happens.

I am missing two color ink cartridges-yellow, magenta.  But changed settings to black copy only.

Should I be able to make a copy of something put on the scanner glass in black? Nothing happens.

If I try to scan to a pc file, the printer LCD is trying to connect to the PC, error message comes up on top of my monitor and it reads printer not connected. 

So I next tried viewing pictures on my SD card placed in the card reader on the printer. When I click on view pictures. Message comes up "Out of Memory".

Not sure if something is wrong with the printer itself, picked it up at a moving sale. It looks almost brand new.


If I go into Printer Configurations under Administ. it shows my printer with a red heart.

Any help will be appreciated.

---

### Post by SVEN1 on 2009-03-02
This printer will refuse to operate in any mode if any cartridge is out of ink. I have two cartridges missing.

I have read that you can fool the printer into thinking it has a full cartridge by using white out on the cartridge ink level indicator. It uses a light sensor to check the level. By covering over the clear level, it thinks it's full.

Loooks like I have to spend $20.00 to get this printer maybe to work.
I'll sell it to someone who has windows....
Think I'll find another printer an HP.

---

### Post by TopEnder on 2009-03-02
> **SVEN1 said:**
> Ok it's installed, I can send a print job to que and it goes to processing, nothing happens.

I am missing two color ink cartridges-yellow, magenta.  But changed settings to black copy only.

Should I be able to make a copy of something put on the scanner glass in black? Nothing happens.

If I try to scan to a pc file, the printer LCD is trying to connect to the PC, error message comes up on top of my monitor and it reads printer not connected. 

So I next tried viewing pictures on my SD card placed in the card reader on the printer. When I click on view pictures. Message comes up "Out of Memory".

Not sure if something is wrong with the printer itself, picked it up at a moving sale. It looks almost brand new.


If I go into Printer Configurations under Administ. it shows my printer with a red heart.

Any help will be appreciated.
Just quick response.  Brother Printers along with many other popular printers/scanners require all the ink cartridges to be installed and with ink in them for the printer to work even if you only want to use the black, by the way the drivers for your MFC are in Synapic Package Manager & they will install any extra packages required.

As for the scanner you could try the following:
What I have set out below works on Ubuntu 8.04 64bit and Ubuntu 8.10 32 bit for a Brother DCP-150C it has been used by other forum member for other Brother scanners models.

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.

Code:
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Save file

4. Restart the system.

&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install: sane-utils if not already installed (it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New
Enter brscan-skey in:
Name: and
Command:
Comment: MFC-440CN or what you want to call your printer/scanner

Press OK and enable the entry.

If you get an error with Xsane close it down open it again and try some tomes it will work, also try using the Scanner Control panel (using SCAN / up butter (scan to file) / OK / Start / Mono or Colour. It should save the file in Home Folder/brscan.

The Brother Web Page has a lot of useful information including most of the above. If you have any problems then feel free to PM me. TopEnder

---

### Post by SVEN1 on 2009-03-03
Will give another try. I removed the drivers downloaded previously and reinstalled the drivers per your suggestion using Synaptic Package Manager.

I will see what changes take place this evening.
Thanks

---

