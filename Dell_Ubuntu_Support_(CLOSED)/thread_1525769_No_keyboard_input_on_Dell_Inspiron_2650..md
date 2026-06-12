---
title: "No keyboard input on Dell Inspiron 2650."
date: 2010-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stormsy on 2010-07-07
Hi there,

I have a copy of Ubuntu 10.04 LTS and tried to install it onto my Dell Inspiron 2650 as the **only** OS on that laptop.  

However, I run into trouble as the keyboard will not work.  I have looked for an update for the keyboard driver, and sadly the driver is up-to-date.

So, I am at a bit of a loose end.  Any thoughts or suggestions are greatly appreciated :)

Thanks,
Stormsy.

---

### Post by mörgæs on 2010-07-13
How does the machine behave, if you boot with a 9.10 live cd? 

[www.releases.ubuntu.com](www.releases.ubuntu.com)

---

### Post by fultoodhamaal on 2010-07-22
I am having the same issue. My 2650 is completely unusable after it boots up. I tried LinuxMint ... same issue. However, when I tried Fedora 13 or openSUSE 11.3, it was ok. I tried with noapic/nolapic but did not help. I still haven't tried with older Ubuntu releases.

---

### Post by fultoodhamaal on 2010-07-23
I tried out "noacpi pci=noacpi acpi=off" and that seem to have done the  trick. I was able to boot and use the keyboard and mouse.

---

### Post by simosx on 2010-07-23
There has been a case with Dell laptops and Ubuntu; when you ran on battery and you start Ubuntu, the keyboard does not respond. The keyboard does respond to enter the BIOS or to select options in GRUB, but it does not work when you enter the GUI.
However, if you power off the laptop, connect to mains and start again, then the keyboard is fine. Can you check whether or not this is your case? It will help to figure out if it's a recurring situation.

---

### Post by Cycledoc on 2010-08-03
I'm very new to Ubuntu using a Dell 2650.  I have had problems with the keyboard and have been managing to turn off acpi with the F6 during the boot.

I am looking for  a more permanent fix and wondering where to add the "noacpi pci=noacpi acpi=off" line?

Ubuntu 10.04 WUBI installation.  

Many Thanks

---

### Post by simosx on 2010-08-03
> **Cycledoc said:**
> I'm very new to Ubuntu using a Dell 2650.  I have had problems with the keyboard and have been managing to turn off acpi with the F6 during the boot.

I am looking for  a more permanent fix and wondering where to add the "noacpi pci=noacpi acpi=off" line?

Ubuntu 10.04 WUBI installation.  

Many Thanks

Have you verified that you have the latest BIOS update installed?
If you need to disable ACPI to get the keyboard working, then it's the BIOS DSDT tables at fault.

It looks like an issue that Dell needs to fix. Google for 'ubuntuforums dsdt' for the discussion on DSDT.

---

### Post by user134 on 2010-11-29
Dell Inspiron 2650 updated to latest bios (A13, 4/8/2004)
Ubuntu 10.04 live CD

Contrary to post above, when I booted on battery power the keyboard was active. When I booted on mains power it was not.

Setting the F6 option APCI=off enabled the keyboard.

---

### Post by user134 on 2011-11-11
When the battery is non-functional (only runs on mains power), the live CD works with the F6 acpi=off command, but I could not get the keyboard to function after I installed to the hard drive until I removed the battery. Then the keyboard works.

---

### Post by sahdow on 2011-12-29
Just started playing with Ubuntu - installed on several older laptops successfully.

Installed 10.04 LTS on Inspiron 2650; once I removed the battery (it's been toast for a while) everything worked correctly.

---

### Post by silva_28 on 2011-12-30
How does the [machine]("http://allinkshort.com/") [behave,]("http://allinkshort.com/") if you boot with a 9.10 live cd? 

[]("http://www.releases.ubuntu.com/")

---

