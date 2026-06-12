---
title: "trying to install operating system .ISO FROM my ipod"
date: 2009-04-21
forum: General Help
---

### Post by Ozzy0sbourne on 2009-04-21
im really kinda new at this.
my computer won't burn dvd's btw.
and im not trying to install ubuntu.
im already running ubuntu 8.10

also before i begin this the .ISO to windows vista is a legal backup that i obtained by extracting the .ISO from the backup disc that they gave me when i got my computer. and now i have lost that backup disc. so i am forced to use the .ISO

what i have done is taken gparted and created a new partition table (msdos) and then i formatted that unallocated space to NTFS... then i restarted and the computer read my ipod as a USB drive. (like i wanted.)
so then i took the .iso and put it on my ipod with drag and drop.

then i restarted. went into bios and changed it to where the usb drive would be booted FIRST.
the screen was black and had a solid grey thick blinking underscore _
and it didn't do anything.

any ideas on how i could it to work with my ipod?

thank you in advance.

---

### Post by Ozzy0sbourne on 2009-04-21
bump urgent :(

---

### Post by Ozzy0sbourne on 2009-04-21
bump this is VEEEEEEEEEEERY urgent

---

### Post by prem1er on 2009-04-21
To boot from the ipod it has to have contain boot/system files otherwise you can't just boot from an iso file.  Do you have a flash drive available?

---

### Post by Therion on 2009-04-21
The .iso data file is not "bootable".  The iso creates a bootable device when it's burned to the device in question as an image.  

You could try burning the .iso you have TO your iPod as an image using Deep Burner or some other iso burner (Nero, whatever you can put your hands on) and see if that will work.

---

### Post by Ozzy0sbourne on 2009-04-21
> **Therion said:**
> The .iso data file is not "bootable".  The iso creates a bootable device when it's burned to the device in question as an image.  

You could try burning the .iso you have TO your iPod as an image using Deep Burner or some other iso burner (Nero, whatever you can put your hands on) and see if that will work.

i see.
so what i need to do is use some program to open the .ISO file and then write an autorun.inf to autorun the setup exe. and put that autorun in the .iso file.

this is my theory since in the ubuntu disc... i opened "autorun.inf" and the text editor showed 

"[autorun]
open=umenu.exe
icon=umenu.exe"


so i guess i can ask one more question.

the question is after i make the autorun.inf file...


do i put the autorun in the .ISO and put the iso on my ipod

or.... do i put extract the .ISO files and put those on my ipod including the autorun file.

---

