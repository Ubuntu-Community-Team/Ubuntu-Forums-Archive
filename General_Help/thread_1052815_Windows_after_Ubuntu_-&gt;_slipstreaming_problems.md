---
title: "Windows after Ubuntu -&gt; slipstreaming problems"
date: 2009-01-28
forum: General Help
---

### Post by Fuwisu on 2009-01-28
Hello,

I've been trying to install Windows after Ubuntu. I already have a full NTFS-partition, but when I boot from the windows xp cd it says it cannot find any hard drives.

I found on google that the problem probably is lack of SATA drivers. So I installed remastersys to slipstream sata drivers (which I haven't found yet, does anyone know what drivers I need for an Acer 5920G?). Now when I start remastersys, it begins to back-up my whole system for some reason. 

Can anyone give me a few tips on how to handle this kitty?

Thanks in advance ;)

---

### Post by geirha on 2009-01-28
The first hit on this google search seems to cover it:
[http://www.google.com/search?q=how+to+install+windows+xp+on+Acer+5920G&btnG=Search](http://www.google.com/search?q=how+to+install+windows+xp+on+Acer+5920G&btnG=Search)

And once Windows is installed, you'll need to reinstall grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Fuwisu on 2009-01-28
"change the BIOS parameter “SATA mode” from AHCI to IDE (you need the BIOS v3708)."

Hmm I don't see that option in my bios, how can I see what version of bios I have?

---

### Post by geirha on 2009-01-28
Depends on the BIOS. Usually it shows it somewhere in the menu. You might be able to see it from Ubuntu, by running ```
sudo lshw | less
``` look for "Description: BIOS"

The manual for the laptop might also have instructions on how to find that information.

---

### Post by Fuwisu on 2009-01-28
Ok apparantly my bios doesn't have that option. Now I'm trying this guide ([http://www.msfn.org/board/index.php?showtopic=13173&hl=Si3112r](http://www.msfn.org/board/index.php?showtopic=13173&hl=Si3112r)), but at one moment he says "The first place to add a copy is to the TXTMODE folder of your CD. That is: "c:\xpcd\$OEM$\TEXTMODE" Here you can dump the 7 Silicon Image files and 4 Intel files." First of all my CD doesn't have such a map, and second of all how can "dump" something on a cd -.^ He doesn't mention any slipstream program...

---

### Post by Fuwisu on 2009-01-28
The main problem now is that I cannot ope nlite under Wine, it doens't do anything :( Maybe it's because it's possible that I don't have the .NET framework, but I wouldn't know how to install those.

---

### Post by Fuwisu on 2009-01-28
Anyone?

---

### Post by Fuwisu on 2009-01-28
Come on there must be an nlite alternative, it's my only option for installing xp :(

---

