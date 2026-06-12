---
title: "Can I update my BIOS through VirtualBox XP?"
date: 2009-01-09
forum: General Help
---

### Post by Charbs on 2009-01-09
Just like the title says.

Im running Ubuntu 8.10 and have XP running in virtualbox. Is it possible to update my laptops BIOS with XP in virtualbox or would that be computer suicide?

---

### Post by kellemes on 2009-01-09
> **Charbs said:**
> Just like the title says.

Im running Ubuntu 8.10 and have XP running in virtualbox. Is it possible to update my laptops BIOS with XP in virtualbox or would that be computer suicide?

You're in a **virtual** box. It's not the real thing ;-)

---

### Post by Charbs on 2009-01-09
So the virtualbox has zero access to the computers BIOS?

I guess id have to install XP onto a seperate partition and do it that way, but thats too much work. The only reason i want to update the bios is becuase ubuntu is not recognizing my battery charge. It always says 0% weather im plugged in and charging, or unplugged and discharging. 

I was hoping the bios update would fix it.

---

### Post by Therion on 2009-01-09
I don't see anything preventing this from working.  

I'm assuming you would simply download BIOS updater and run it in your XP guest much like any other Windows app.

---

### Post by Charbs on 2009-01-09
ya thats exactly what i want to do. i have the .exe file which is an auto-updater. but i just wanted to ask around to see if its ever been done before cuz i didnt want to attempt it and destroy my laptop in the process.

---

### Post by shad0w_walker on 2009-01-09
Virtual machines are entirely simulated. The bios that guest XP would have access to is a virtual, simulated bios. It will not work. Been there, considered it.

I would suggest looking at a dos bootable disk or some such, almost all bios updaters have a dos version, which you could easily run off floppy.

---

### Post by Charbs on 2009-01-09
well is there even a little risk in running the update.exe in the virtualbox, cuz i wouldnt mind just trying it to see what happens, but not if its gonna kill my lapop.

---

### Post by shad0w_walker on 2009-01-09
If it did anything at all, I'd be thoroughly amazed. It can't harm your laptop, that's a key advantage of a virtual machine. It's completely separate from the real thing, making it a great way to avoid viruses and other nasties hiding in software.

---

### Post by Charbs on 2009-01-09
ya im not worried about it harming my linux OS, or any files on it. Im more worried about it TRYING to access my mobo and TRYING to half-*** update the bios and fail halfway through the update turning my laptop into a paperweight.

---

### Post by chrisinspace on 2009-01-09
> **shad0w_walker said:**
> Virtual machines are entirely simulated. The bios that guest XP would have access to is a virtual, simulated bios. It will not work. Been there, considered it.

I would suggest looking at a dos bootable disk or some such, almost all bios updaters have a dos version, which you could easily run off floppy.

I would agree with shad0w_walker.  The virtual machine doesn't see the underlying hardware.  For example if you check your xorg config files, you'll see that it refers to vboxvideo, vboxmouse, etc.

I wouldn't recommend running the executable BIOS updater in a virtual machine.  If you check the MoBo manufacturer's site, they should offer a bootable floppy.  I know a lot of laptops don't come with a floppy anymore, but you could download the files for the bootable floppy, and use them to create a bootable cd.  Then update your BIOS from the cd.

---

### Post by Charbs on 2009-01-09
I dont really NEED to update the BIOS, my main problem is this:

[http://ubuntuforums.org/showthread.php?p=6524003#post6524003](http://ubuntuforums.org/showthread.php?p=6524003#post6524003)

I just thought that maybe updating the bios would fix my problem, but im starting to think it wouldnt help and not worth the risk.

If i can figure out that other problem then the bios update would be pointless.

---

### Post by jmontelius on 2009-01-09
Some BIOS has update features built in to them. Restart the machine and step into the BIOS setting. Any thing that reads "Tools" or "Update"? If so you should be able to locate the new bios (probably not the .exe file) on a USB stick and do the update.

---

