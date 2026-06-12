---
title: "Ubuntu 10.10 - Dell Inspiron M5010"
date: 2010-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ivangodfather on 2010-11-29
Hi, i recently bought a M5010. I tried to install ubuntu 10.10, with no succeed. I tried 64bits full image, 64 alternate and the 32 bits image. When i boot from CD it starts the installation cd and then i get a black image with the 3 cds. any ideas? i tried those in other laptos and all is fine...

---

### Post by mikewhatever on 2010-11-29
M5010 is very informative. What is it?

---

### Post by gibbylinks on 2010-11-30
Do you hear any sounds ?

Is it booting and asking for login ? (You would here the default login sound)

---

### Post by ivangodfather on 2010-11-30
Its the "Inspiron™ M501R (N00M5009)".
I dont hear anything. I cant choose the language installation neither.

---

### Post by ivangodfather on 2010-11-30
When it starts booting from CD, i see a first logo of ubuntu and then it gets black with no activity, then theres no login sesion or similar, (i wait several times more than 10 min). Other PCs boot those cds normally.

---

### Post by locosway on 2010-12-01
I too just bought a M5010 from Best Buy and I can't get the Ubuntu installer to load up. I've been using Linux for 10 years, and while I have seen problems like this on bad hardware, I didn't expect it on a new laptop.

---

### Post by locosway on 2010-12-02
Appending acpi=off works to get Ubuntu installed, and booting after installation.

Only problem is I need ACPI turned on, so this really sucks.

Does anyone know of any work arounds for turning off acpi? This seems to be an issue with AMD laptops from what I've seen, kinda odd.

---

### Post by Zomp on 2010-12-02
Ubuntu 10.04 installation worked for me. Then I upgraded to 10.10 but I had to change the default kernel to older one (I suggest to fully update 10.04 before upgrade to 10.10 to have at least a little bit newer kernel). Wired ethernet didn't work for me, but wireless works. I had to manually compile drivers and it is working now (it is probably fixed in the new kernel, but I haven't made out how to use it).

---

### Post by locosway on 2010-12-05
So far the workable fix for this is using:

pci=noacpi

Use this to boot the install CD, and to boot your HDD once Ubuntu is actually installed.

I have all three cores working, and everything else seems to be working correctly. On a side note, Fedora runs on my laptop just fine without turning off ACPI, so there's likely a perminent fix in the kernel via a module or compiled in that we should be able to turn on.

---

### Post by alang184 on 2011-02-10
I've got this exact same problem. Just bought an M5010 with AMD Phenom, and Ubuntu disc won't boot; just hangs after a few seconds.

So with the suggestion of disabling ACPI, how can this actually be done? I've looked around the BIOS setup, but nothing on ACPI.

Some of the BIOS options that I tried disabling:

'PowerNow!'
'Virtualization'

Tried changing SATA operation from 'AHCI' to 'ATA'. Didn't solve the problem.

---

### Post by GeorgieDob on 2011-02-11
Hiya all, 
We got the same model this morning and after messing about managed to install 9.10 then 10.10.

On start up of machine press F12 to access the boot menu. 
Wait for the cd to stop. (tried a few times with it still reading and it didn't work)
Select cd/dvd, enter, then hold down F12 again.
The language window should pop up. 
Select your language. 
Press F6 and select acpi off, Esc
Then install as normal. 

I would love to know why this works if anyone has any ideas. 

Hope it works for you all. 
Georgina.

The belief in a thing makes it happen - Frank Lloyd Wright
Once begun is half done - Mary Poppins

---

### Post by GeorgieDob on 2011-02-11
Hi,
next bit.....

After installing if this still gives the black screen. 
At the grub os menu select e to change the grub settings. 
Put pci=noacpi  at the end of the line where splash is written. 
CTRL X to boot. 

For the permanent fix. 

cd /etc/default
sudo cp grub grub.backup  (just in case it goes wrong)
sudo gedit grub
change this line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for this
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"
save

then run 
sudo update-grub

Hope this helps and works for you. 
Georgina.

---

### Post by wheresjim on 2011-02-11
This is from memory, so it may be a little off, but this is how I remember I did it on my M5010, though I just did it a few days ago (standard disclaimers about fitness of this info apply):

When the purple screen comes up after starting with the DVD press any of the F buttons (f1, f2, f3 etc.) and the options menu will pop up.  Select F6 and choose pci=noacpi.  Then boot, you should be able to boot the DVD that way to install.  

Afterwards you will need to boot using acpi=off so when it starts to reboot after install, hit the f buttons again immediately after the dell boot screen disappears, that will get you into the grub menu.  Select "e" so you can add acpi=off to the boot configuration for the next next boot (add it immediately after so that "quiet splash" -> "quiet splash pci=noacpi").  Now hit ctrl-x to boot using that configuration.

Now that it has booted into ubuntu, you need to edit your grub configuration permanently.  Type "sudo gedit /etc/default/grub" and add "pci=noacpi" to the line starting with "GRUB_CMDLINE_LINUX" so that line looks like "GRUB_CMDLINE_LINUX="GRUB_CMDLINE_LINUX"" (the pci=noacpi part is in quotes on the line).  Now save and close that file and type sudo grub-update and let grub update it's configuration.

You should be able to boot normally after that. 

Now if I could only get the stupid wireless to work!

---

### Post by Slicestrider on 2011-02-13
Hi I just got a Phenom X4 M501R this weekend and got Ubuntu 10.10 64bit to install quite easily. The only thing I had to do was go into the bios and swtch USB emulation to disabled. Before I did this it would just hang on trying to start the CD.

---

### Post by sibyphilips on 2011-02-28
Hi, 
I have the same problems detailed in the post (on my Phenom X4, M5010), namely the 10.10 bootable USB drive leads me to a blank screen and do not allow anything more, I thus Installed 10.04 without any problem and then tried to upgrade to 10.10, and used the "pci=noacpi" as detailed here and then booted upgraded grub etc etc, but the problem started now, the laptop fan was running heavily and the system was getting heated producing a lot of noise, finally I reinstalled 10.04 and now the system runs fine.
Installing/booting into 10.10 is solved by pci=noacpi, but what could we do to reduce the heat/sound, or is it better to stick on to 10.04 until the next LTS
thanks,
SIBY.

---

### Post by syednizamudeen on 2011-03-10
Me too..same problems...i dont wanna use it on ATA..i just want it with ahci...i can wait for the fix

---

### Post by Philippos21 on 2011-03-23
Now that it has booted into ubuntu, you need to edit your grub configuration permanently.  Type "sudo gedit /etc/default/grub" and add "pci=noacpi" to the line starting with "GRUB_CMDLINE_LINUX" so that line looks like "GRUB_CMDLINE_LINUX="GRUB_CMDLINE_LINUX"" (the pci=noacpi part is in quotes on the line).  Now save and close that file and type sudo grub-update and let grub update it's configuration.

Can you write the exact command that you write on the terminal?And can you tell me a way to uninstall the ubuntu if i need to?

---

### Post by Philippos21 on 2011-03-23
Can you write the exact command that you write on the terminal

---

### Post by ernieg92 on 2011-04-07
I, too, recently bought this laptop and was hoping to get the latest Kubuntu installed.  Had to go with 9.10.

Like wheresjim, my wireless isn't working.  I can toggle the wireless on and off via the keyboard, but no wireless networks show up. Has anyone found a fix for that?  

Also, are there any dangers running with pci=noacpi?  I'm only using it for short periods right now (since wireless is not working) but if I start to use it more I don't want to damage the laptop.

Thanks in advance for any help!

---

### Post by aliasandy on 2011-04-17
I have the m5010 also, and it will boot the live cd when acpi is off, but it doesnt know when its running on ac or battery, no problem I guess ill just keep my charger around, but when I install how do I get into grub to turn off acpi? Sorry for the late post and probably simple question, ive never used linux before, I also appologize for spelling errors etc, I am on my phone currently.

---

### Post by blaede22 on 2011-10-13
My girlfriend has the same laptop and we've had endless problems with it and Ubuntu (and elementary OS). It seems that it's just not a very wonderful machine, though it seems to be possible to get things working.

I disabled ACPI for the install, then for the boot. But now the battery isn't detected (since it has something to do with ACPI). Does anyone know how to get that working again?

---

### Post by locosway on 2011-10-13
> **blaede22 said:**
> My girlfriend has the same laptop and we've had endless problems with it and Ubuntu (and elementary OS). It seems that it's just not a very wonderful machine, though it seems to be possible to get things working.

I disabled ACPI for the install, then for the boot. But now the battery isn't detected (since it has something to do with ACPI). Does anyone know how to get that working again?

You're right, it's not the best laptop for Linux. I've had a lot of issues myself, and ended up running Windows 7 for 6 months or so.

What you're looking for is "acpi=noirq" as a boot flag, this will solve most all problems with this laptop.

---

