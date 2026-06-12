---
title: "Wanto to remove Ubuntu and install Windows XP"
date: 2008-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sr20fd3st on 2008-11-02
Hello.
I bought a dew Dell about a year ago or so and it came with Ubuntu.  I would like to remove Ubuntu and install Windows XP.  I tried to change the boot order so the CD would boot first but this didn't work for whatever reason. Then I tried opening the setup.exe file on the CD after Ubuntu loaded up and the setup froze and came to a blue screen.  Is there a boot disk or something that I can use to get the computer to boot up into DOS or some form of a command prompt to where I can access the CD drive and load the setup.exe file from there?  

Thank You.
Oliver

---

### Post by rage-against-windows on 2008-11-02
First off you will have to go to the Dell website and download all the appropriate drivers XP will need for your system. When you go into the hardware setup make sure you save our changes first before exiting after you set your CD to boot first and it should work. Make sure you have your XP disc inserted before you power up. Dont forget to visit Dell first to get ALL our drivers because after you install XP all you will have is a base OS and a whole load of hardware errors to deal with. I think after you go through all this XP installing and get it set up and use it a couple weeks you'll be wanting Ubuntu back.

---

### Post by sr20fd3st on 2008-11-02
The computer doesnt seem to recognize the fact that the CD is a boot disk.  It is set to boot from CD.  Therefore I need some sort of floppy disk that will let me initialize the setup.exe file from the CD BEFORE ubuntu has loaded. This way I can reformat the whole disk, set it to NTFS and install Windows. 

Thanks

---

### Post by mike555 on 2008-11-02
If your sure this is what you want to do, get the dell drivers and save on a CD , get a ubuntu live cd and boot from it , then use gparted to partition and/or format your hard drive ... restart with the Windows install disk and install ......

---

### Post by sr20fd3st on 2008-11-02
Thanks

I am only worried though, that since it is not reading the CD to boot from it NOW that it also will no boot from it after i reformat it, which would leave me in this same predicament.

That is why I was hoping there was a Floppy Boot Disk or similar Floppy utility that could be used to open the setup.exe file on the CD.  I just need some way of accessing the CD drive files prior to Ubuntu booting up.

Thanks again,
Oliver

---

### Post by gbrainin on 2008-11-02
Microsoft has an article on creating a boot floppy for Windows XP: [http://support.microsoft.com/kb/305595]("http://support.microsoft.com/kb/305595").

Before you do that, you mentioned that having the machine boot from the CD did not work "for whatever reason."  What happened instead?  Did you get an error message that the CD was not bootable, or did the computer boot from the hard drive?  If you got a not-bootable message, your CD may be bad, and you should look into getting a different one before you try loading the OS from it.  If it booted from the hard drive, are you 100% sure you changed the right settings to boot from the CD?

---

### Post by sr20fd3st on 2008-11-02
It simply booted to Ubuntu, ignoring the CD.  

I am sure the CD is good I have used it on another computer recently.  

Will the computer, with Ubuntu as an OS, recognize a Windows XP boot disk during startup?

If i throw a windows 98 boot disk in there will it get me to a command prompt (i dont know if it will be DOS or something by Ubuntu) to where i can select and open the contents of the CD

Thanks

---

### Post by Muflon on 2008-11-03
> **sr20fd3st said:**
> Will the computer, with Ubuntu as an OS, recognize a Windows XP boot disk during startup?

The boot process (from a CD) takes place before the OS on your hard disk is accessed.  The Ubuntu OS that you have installed won't enable or disable the CD from booting because at that point it isn't running.

Muflon

---

### Post by gbrainin on 2008-11-03
If you're sure the CD is good (bootable), then the most likely cause is the BIOS settings not being correct.  Without knowing the specific computer model you have, exact instructions are difficult, but with most recent Dells you can change the boot order on a one-time basis by pressing F11 when the Dell splash screen shows up (the same time you press F2 to get to the BIOS setup).

After pressing F11, you should get a list of bootable items that you can select from.  Choose the CD drive, and it should boot off the XP CD, allowing you to load without the need for a boot floppy.

If that doesn't work, I'd suggest trying the Microsoft instructions for creating a boot floppy.

---

### Post by sr20fd3st on 2008-11-03
actually this is for someone elses computer, far away from me.  I cant see it for myself so its tough to talk them through it.

they just informed me there is no floppy, so i guess iw ill ahve to keep trying to boot it from the CD.

Thanks for your help,

Oliver

---

### Post by aklv47 on 2008-11-03
first if u still have ubuntu on sys then open terminal and type 
sudo fdisk /dev/sda
if this shows cylinder size more then 1024 then xp wont boot from the HD
LIVE CD won't help u here
get either open suse or alternate ubuntu installation cd (i have used open suse) and create partition with cylinder size 1024 
it has to ur primary partition as XP installs on primary partition only

---

### Post by sr20fd3st on 2008-11-09
cylinder size shows to be 30394.  


so what exactly do i have to do for windows to boot (ie change it to 1024?)


It gave me the option to delete partition, should I do that and then pop in the OpenSUSE cd and boot from it and then create a new primary partition with cylinder size 1024?

or should I NOT delete partition and just use the OpenSUSE cd during boot and format the disk and then make the new partition all at once?

---

### Post by sr20fd3st on 2008-11-11
anyone?

---

