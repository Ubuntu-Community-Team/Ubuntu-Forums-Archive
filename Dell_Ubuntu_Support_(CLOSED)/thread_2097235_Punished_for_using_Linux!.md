---
title: "Punished for using Linux!"
date: 2012-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hogfan on 2012-12-22
Why are we punished for using a Linux OS?  I have a Dell XP 14Z that I need to apply two updates to.  I need to upgrade my BIOS from A03 to A06, and I also need to apply a Seagate firmware update that resolves and issue with the HDD spinup time.  I have spent over 4 hrs on this because Dell will not provide DOS based update utilities.  Why do I HAVE to be running Windows to update firmware on my Dell laptop?  I was able to fire up my WIN7 VM, download and intstall the Windows AIK and built a WINPE Live disc with WIN PE 3 tool, including the two executables for the BIOS update and the Seagate firmware update.  

After booting from the disc I am able to load both programs, but the stupid Dell BIOS update utility Insyde Flash  won't let me flash the BIOS because it says the battery is not installed and the laptop is not plugged in to A/C power.....even though it is!  (sure it related to PE not seeing either).  Seagate utility just errors out and tells me to read the documentation.  I am irate now!  

Is there no other solution other than using Clonezilla to take a complete image of the HDD, Install Windows 7 over my perfectly working Linux install, update the stuff I need to, and then completely re-image the drive back to my linux OS, and hope GRUB plays nice at boot?   This is so frustrating!  I am far from a beginner user.  I run OSX, and Linux OS now primarily.  In the past I have done large scale network support for Windows domains, etc., but this issue takes the cake.  Dell is basically saying "We don't care about your hardware support if you aren't using Windows!".  Suggestions?

Thanks.

-hogfan

---

### Post by kurt18947 on 2012-12-22
It's a pain but at the same time I can sort of see Dell's position.  It isn't like there are millions of Linux users that don't also have a Windows partition.  However, I wonder how hard it would be to have a very stripped down bootable CD/ USB image that would make the update self booting/self installing.  FreeDOS?  That would take any potential Windows problems out of the upgrade process.

---

### Post by Lars Noodén on 2012-12-22
The last time I had to do a BIOS update, FreeDOS worked on a floppy.  If your machine does not have a floppy then there is a way to get FreeDOS to work with grub:
[http://ubuntuforums.org/showpost.php?p=12167567&postcount=8](http://ubuntuforums.org/showpost.php?p=12167567&postcount=8)

---

### Post by lykwydchykyn on 2012-12-22
Dell actually provides some tools to install BIOS updates in Linux; I don't know for sure that it will work with your model, it's mainly intended for servers.  But I've used it on my laptop and several desktops successfully.

Basically, you install the smbios-utils package and the firmware-addon-dell package.  Use firmwaretool to extract an hdr file from the BIOS update file, then use the dellBiosUpdate command (from the smbios-utils package) to install it.

Here's a partial tutorial here:

[http://allurgroceries.com/dellbios.html](http://allurgroceries.com/dellbios.html)

They use wine to extract the hdr file from the bios, but I think it can be done with firmwaretools.  Haven't tried that part of it myself.

---

### Post by ckruetze on 2012-12-25
We always use a FreeDos USB stick for BIOS updates on our Dell Hardware.
It works perfect and is extremely fast. In addition to that the OS isn't changed in any way, there are no packages drivers or anything else installed.

Here is a step by step guide how to do it


[LIST=1]
[*]First, you need to create a FreeDOS bootable USB-Stick. Install UNetbootin from synaptic or type in the following command:
```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin

```
[*]Plug in a USB stick, run UNetbootin and create a FreeDOS USB stick.
[*]Download the latest DELL-BIOS_MODEL.EXE file and transfer it to the stick.
[*]Reboot and enter the BIOS-options (F12) to choose your USB-device.
[*]Choose the "FreeDOS Safe Mode (don´t load any drivers)" option.
!!! Do NOT choose to install the FreeDOS or any other special options like HIMEM or EMM386 !!!
[*]Type "c:" and "dir" to get the list of all directories and files on your stick.
[*]Type your BIOS and hit <ENTER> to execute the BIOS-update.
[/LIST]
If you plan on using this USB stick a lot, you could speed it up by changing the FreeDos boot menu to automatically do Step 5 and remove the install options.


Hope this helps,


Christian

---

