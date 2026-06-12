---
title: "BIOS update on Dell E6410"
date: 2010-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dargaud on 2010-12-01
Hello all,
I've been trying to perform a BIOS upgrade on a DELL Latitude E6410, but none of the instructions I could find work.

First I tried downloading E6410A05.exe from Dell's website and extracting the HDR file as stated in many instruction pages:
```
$ wine E6410A05.exe -writehdr -nopause
Unrecognized option: -writehdr

```

Then I followed [those instructions]("http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2007/12/05/37446.aspx"):
```
# aptitude install $(bootstrap_firmware -a)
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x3b07-subven-0x1028-subdev-0x040a"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x3b07-subven-0x1028-subdev-0x040a"
...[3 pages like that]

# update_firmware
Running system inventory...
Searching storage directory for available BIOS updates...
Checking System BIOS for Latitude E6410 - A03
        Did not find a newer package to install that meets all installation checks.
This system does not appear to have any updates available.
No action necessary.

```
Well, there IS an update available: A05

---

### Post by nbubis on 2011-06-20
Hi,

I haven't tried this yet, but apparently you can:
1. [create a freeDOS usb stick]("http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/") 
2. copy the E6410***.exe file onto it.
3. boot from the usb
4. run the EXE file and reboot.

---

### Post by hawthornso23 on 2011-06-22
Yeah, Dell seems to have not compiled the -makehdrfile option into their more recent BIOS updates. They've also abandoned their linux BIOS update site, which is now suffering from bitrot. To be honest I don't know why we bother having a Dell Support forum any more since there isn't any Dell linux support that I can see. In fact it is more like Dell are actively obstructing linux at present. This is exceedingly annoying. My next machine will NOT be a Dell. 

This is the method I used to update BIOS on my E6510

1. Install UNetbootin from synaptic
2. Run it and create a FreeDOS USB key.
3. Copy the exe BIOS update file to the USB key from inside ubuntu.
4. Reboot into BIOS setup and change the boot order to boot from USB
5. Boot into a live freedos session. 
      * The USB key will offer to install freedos on your hard disk.  DONT - that is ubuntucide!
      * Don't use himem or or that other memory thingywhatsit - just straight freedos
6. C: 
7. dir
8. run the update

Good Luck

---

### Post by dargaud on 2011-06-23
Thank you, that was easy to follow and rather painless.

---

### Post by sgreimer on 2011-08-16
That was very helpful, thanks.

---

### Post by mrv on 2011-09-05
For me the system just seems to hang after changing to c: and entering the dir command :( No output and no possibility to run the .exe. Running Ubuntu 11.10 normally, ie. from where I executed unetbootin.

---

### Post by frogotronic on 2011-12-26
> **hawthornso23 said:**
> Yeah, Dell seems to have not compiled the -makehdrfile option into their more recent BIOS updates. They've also abandoned their linux BIOS update site, which is now suffering from bitrot. To be honest I don't know why we bother having a Dell Support forum any more since there isn't any Dell linux support that I can see. In fact it is more like Dell are actively obstructing linux at present. This is exceedingly annoying. My next machine will NOT be a Dell. 

This is the method I used to update BIOS on my E6510

1. Install UNetbootin from synaptic
2. Run it and create a FreeDOS USB key.
3. Copy the exe BIOS update file to the USB key from inside ubuntu.
4. Reboot into BIOS setup and change the boot order to boot from USB
5. Boot into a live freedos session. 
      * The USB key will offer to install freedos on your hard disk.  DONT - that is ubuntucide!
      * Don't use himem or or that other memory thingywhatsit - just straight freedos
6. C: 
7. dir
8. run the update

Good Luck

Hi,

  This worked incredibly well - Thanks!!

- CH

---

### Post by lazier on 2012-05-09
Thanks for the detailed instruction. However, my laptop apparently does nothing at the last step. I type the exe file name and press ENTER. A new line opens and it stays thay way. After 10 minutes, i rebooted using ctrl alt del. What could be the problem? I am trying to upgrade from A05 to A09.

---

### Post by dunbrokin on 2012-07-18
> **lazier said:**
> Thanks for the detailed instruction. However, my laptop apparently does nothing at the last step. I type the exe file name and press ENTER. A new line opens and it stays thay way. After 10 minutes, i rebooted using ctrl alt del. What could be the problem? I am trying to upgrade from A05 to A09.


Maybe you need to go from A05 to A06 and so on until you get to A09. Maybe you cannot leave out the intermediate steps.

---

### Post by bela83 on 2012-08-02
> **hawthornso23 said:**
> Yeah, Dell seems to have not compiled the -makehdrfile option into their more recent BIOS updates. They've also abandoned their linux BIOS update site, which is now suffering from bitrot. To be honest I don't know why we bother having a Dell Support forum any more since there isn't any Dell linux support that I can see. In fact it is more like Dell are actively obstructing linux at present. This is exceedingly annoying. My next machine will NOT be a Dell. 

This is the method I used to update BIOS on my E6510

1. Install UNetbootin from synaptic
2. Run it and create a FreeDOS USB key.
3. Copy the exe BIOS update file to the USB key from inside ubuntu.
4. Reboot into BIOS setup and change the boot order to boot from USB
5. Boot into a live freedos session. 
      * The USB key will offer to install freedos on your hard disk.  DONT - that is ubuntucide!
      * Don't use himem or or that other memory thingywhatsit - just straight freedos
6. C: 
7. dir
8. run the update

Good Luck

Hi !

Worked great on a Latitude D620.
Updated directly from A02 to A10.

Thanks a lot :)

---

### Post by edcompsci on 2012-10-31
I haven't tried this yet, but from this link: [http://thoughtsdaily.wordpress.com/2011/11/01/update-dell-bios-in-ubuntu/](http://thoughtsdaily.wordpress.com/2011/11/01/update-dell-bios-in-ubuntu/)

they did this:
[INDENT]sudo apt-get update
sudo apt-get install smbios-utils
[/INDENT] Then, get the System ID:
 [INDENT]sudo getSystemId
[/INDENT] You will get an output like this: (from my Dell Optiplex 760)
 [INDENT]Libsmbios version: 2.2.28
Product Name: OptiPlex 760
Vendor: Dell Inc.
BIOS Version: A12
System ID: 0x027F
Service Tag: 860774J
Express Service Code: xxxxxxxxxxx
Asset Tag:
Property Ownership Tag:
[/INDENT] You will only need the System ID,
go to [http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/) and search for the System ID.
There will be multiple choices, get the one with the BIOS version you want.
Click on it and download the bios.hdr file.
 To install the BIOS file, we have to activate the dell update service, (if there is no output, the service is activated)
 [INDENT]sudo modprobe dell_rbu
[/INDENT] Tell the update tool what to do:
 [INDENT]sudo dellBiosUpdate -u -f /place/where/the/bios/is/bios.hdr
[/INDENT] You are ready now and can restart the computer. The new BIOS will be  installed at the first boot, this can take some time (it took me 5  minutes).
 This way, you don’t have to struggle with a floppy disk or a Windows installation.
 Done




so if I can just extract the hdr file from the .exe then I am going to try this on my Dell Latitude D430, unless anyone has any warning against it.

---

### Post by Eagle3 on 2013-05-06
Thankyou edcompsci, I can confirm that a BIOS upgrade was succesfull on a Dell Inspiron 1545 (sys-id 0x02aa) using Ubuntu.
I had been trying freeDos but kept getting invalid drive C: , so couldn't run the exe from Dell. We shall see if the touchpad intermittent failure stops happening.

---

### Post by trfie on 2013-06-09
hawthornso23's procedure using freedos also works great on linux mint 14 with a dell latitude e6410. I had to upgrade from A04 to A09 as it wouldn't allow going straight to A14. I don't think the other solution will work with the new dell BIOS because .hdr's don't seem to be available for the e6410 from the above link nor does it seem possible to extract them from the newer dell BIOS executables.

---

### Post by emeraldgirl08 on 2013-12-08
> **hawthornso23 said:**
> Yeah, Dell seems to have not compiled the -makehdrfile option into their more recent BIOS updates. They've also abandoned their linux BIOS update site, which is now suffering from bitrot. To be honest I don't know why we bother having a Dell Support forum any more since there isn't any Dell linux support that I can see. In fact it is more like Dell are actively obstructing linux at present. This is exceedingly annoying. My next machine will NOT be a Dell. 

This is the method I used to update BIOS on my E6510

1. Install UNetbootin from synaptic
2. Run it and create a FreeDOS USB key.
3. Copy the exe BIOS update file to the USB key from inside ubuntu.
4. Reboot into BIOS setup and change the boot order to boot from USB
5. Boot into a live freedos session. 
      * The USB key will offer to install freedos on your hard disk.  DONT - that is ubuntucide!
      * Don't use himem or or that other memory thingywhatsit - just straight freedos
6. C: 
7. dir
8. run the update

Good Luck

Thanks for the mini-tutorial Hawthornso23!

I have never done a BIOS update using this method so I am smidgen nervous. I have some questions for you or for anyone else who could contribute. I will be receiving a Dell E6510 in a couple of days and so far I have downloaded the EXE for A09 and A15 (the latest BIOS). The E6510 I will be receiving has BIOS A05. The most recent version is A15. Per the instructions on the Details page for Dell E6510 BIOS update there is a message that states "Please note that if the A08 or before A08 BIOS is currently installed on your system you must first update to A09 BIOS and then flash to the latest A-rev BIOS." My guess is that I need to flash A09 first followed by A15(?)

I am used to the ThinkPad method which was using a downloadable ISO image that I could burn to make a bootable BIOS update disk. For clarification I am not sure what steps 2 and 3 are asking. I have the latest UNetbootin and am slightly familiar with it however I am not sure how to "Copy the exe BIOS update file to the USB key from inside ubuntu." I will be running UNetbootin from a windows laptop. I have UNetbootin open now and see FreeDOS 1.0 and then have the choice of which type of media to install FreeDOS 1.0 to. What I am unsure about is how to "Copy the exe BIOS update file to the USB key." Could anyone tell me how to do that while running UNetbootin in windows? Also I would be installing FreeDOS to a bootable CD (I have a couple of blank ones around but no spare USB drive). 

I also realize the E6510 is fairly old in laptop age so I am not sure if it is used by many forum members here on Ubuntu forums. Regardless I am posting hoping someone might be able to help. Thanks :KS

---

### Post by rexmo on 2014-05-06
BIOS UPDATE for Dell D620:  linux based bios.hdr method worked for me while the freeDOS method did NOT.

---

