---
title: "Ghost login screen"
date: 2009-01-06
forum: Desktop Environments
---

### Post by zilog_z80a on 2009-01-06
in replay to [http://ubuntuforums.org/showthread.php?t=257416]("http://ubuntuforums.org/showthread.php?t=257416") 

to bantamsilver user

bantamsilver wrote:

> 
Ghost login screen
Have loaded Ubuntu on aging P111 Vectra with MGA 200 graphics.The logon screen shows ghost image.It would appear that the correct drivers are not being loaded.Any help would be appreciated.Thanks



the solution for this problem is simple, you have to edit your xorg.conf file and add this line in the Section "Device"

```

        Option          "OverclockMem"

```

your xorg.conf must look aprox like this:

```

Section "Device"
        Identifier      "matrox"
        Driver          "mga"
        BusID           "PCI:1:00:0"
        Option          "OverclockMem"
EndSection

```

reboot your pc and ready!! that's makes the trick!!!

cheers!!! :)

---

