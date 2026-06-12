---
title: "triple boot"
date: 2009-04-17
forum: General Help
---

### Post by ericsizer on 2009-04-17
for the last little while ive been trying to triple boot
ubuntu 8.10
linux mint 6
windows XP home edition

i followed this [link]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5") 

and i did the changes asked of me in linux mint...i realize now that wasn't the best choice because the only OS that will show up in GRUB is the ubuntu one....

Mint 6 and Ubuntu are on a primary HDD while Windows XP is on the secondary

i need help resolving this issue...can anybody help?

---

### Post by Neobuntu on 2009-04-17
Summarily, I think you need to decide which "Linux" partition is your main one, go to that one and do a reinstall of GRUB. Preferably, NOT manually. It should recognize the others and set them all up on your boot (GRUB) menu (calling stage Two from your selected partition).

If you want to get fancier than that. You can customize your main (It's got to live somewhere) partitions  GRUB "menu.lst" to call whatever is in each partition (like it does WIndows). That way, your other "Linux" partition will have it's own "regular menu" AFTER being called from then main boot menu. This would be installed (completely) to the partition (BEWARE that erases the boot sector/OS and usually necessitates a tricky backup and reinstall of the OS).

NORMALLY, **you would NEVER do anything *accept* "setup (hdx)" (One numeral with MANULAL GRUB setup).** With manual GRUB, this is tricky because the "root" command does use Two numerals. Get that straight now. IT HAS NO WARNING!!!!! IF you are installing GRUB (stage 1 is on the MBR) to ANYTHING accept the MBR (Master Boot Record, and that's different than partitions), you should BACKUP all critical boot sectors for EACH critical OS partition. You'll be sorry if you don't. Back up, is the only fix. Always have the data you can't live without backed up FIRST, right?

There are numerous menu (multi-partition) options and they all take time! ...Best to keep it simple. Don't install GRUB manually. Use the installer. It's easy. If you don't want or just don't use more that Two partitions regularly, Just follow suggestion One above.

Multiple partition are time consuming but Two, I recommend for the best of both worlds. It's Simple and the installers will make the other "swap" partition for you, given the blank; not partitioned space)  

Having NUMEROUS partitions/OS'es, is optionally done with a separate boot partition; just for boot menu-ing. I wouldn't, unless you're going for a record of multi-partitions.

If you are doing this because you don't want to wipe your old partition to do the preferred, clean install of a new release, then you are wise. I can't recommend release upgrading, although it can work. It's betting. It's not faster and you can't start at square-one (when bugs arise) without a clean install.

---

### Post by ericsizer on 2009-04-17
i want Mint as my main...but i can't get it to boot, the only options on the GRUB boot are ubuntu and XP..and XP wont boot i get an error msg so technically all i can use is ubuntu

---

### Post by bodhi.zazen on 2009-04-17
See this thread for lots of good advice of multibooting : 

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by powder on 2009-04-17
Please post output of > sudo fdisk -l

---

### Post by Neobuntu on 2009-04-17
My guess is, Mint (asked which perhaps?) then wrote to the MBR of your lone XP hard drive(not booted first. Perhaps never booted; so this MBR is not used.), else wasn't written to any MBR. So you have the old Ubuntu and XP grub menu from Ubuntu, as before.  

All this is very do-able. What you've created can be confusing, so be patient.

At (old) GRUB menu after boot, just hit "c" before it times out.

Where "hd0" is the first DRIVE and the "x" in (hd0,**x**) is 0 or 1, 2, 3, 4, 5 or etc..., position of your Minty partition.

If you do not already know the mint partition number (for GRUB), you can use...> find /vmlinuz Both your Ubuntu and Mint should have this; to help you find the right one for Mint. If you get the wrong one, you can just do it again (**as long as you ONLY use one numeral with "setup"!**) If Mint is your third partition it would be "2". This because GRUB includes, from zero. Remember to check for swap partitions. Mint may have created an unnecessary, second swap partition, and there's probably an "extended" place-holder partition now, so you can have more than 4 partitions on your boot drive (hd0). 
type > root (hd0,x)
**setup (hd0)**

The "root" command will let you know if it found GRUB files to setup. 
After setup (hd0), GRUB will let you see if it wrote successfully.
Reboot and let us know.

**DO NOT get the setup command wrong and as I said if something goes wrong, you better have a backup.**

This should use the mint GRUB and it's settings and put it on you boot-able drives MBR. This is what I think you want. If you get the same menu, you got the wrong one, just try again. All three should be represented. If XP is then missing from the GRUB start-up menu, that's easy to manually add to your "menu.lst" test file. The one in the Mint partition "/boot/grub/menu.lst".

---

