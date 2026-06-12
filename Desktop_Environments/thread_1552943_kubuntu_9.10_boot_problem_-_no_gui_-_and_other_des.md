---
title: "kubuntu 9.10: boot problem - no gui - and other desktop app issues"
date: 2010-08-14
forum: Desktop Environments
---

### Post by sinfaut on 2010-08-14
Hi All,
 
This is my first post and I just registered today.

I was running kubuntu 7.10 from 2007 till two days back. Thought it  quite old, so wanted to upgrade from 7.10 to 9.10, and if I like the  latest kde 4 (since I've not used it yet), the plan was to use the lucid  lynx. The two phase upgrade from 7.10 -> 8.04 -> 9.10 went  seamlessly without any hitch. But now the problem started to occur, and I  will point them one by one:
 
1. While booting, the startup splash screen falls into a console which  read "checking battery state ... DONE" and it stays there forever. So, I  opened another terminal by ctrl-alt-F1, gave my login id, password,  type startx to go into the graphical mode.

I checked the /etc/kde4/kdm/kdmrc file and made the
  Code:
  UseTheme=true

line to **false**. 
 
I Also tried the other suggestions like restarting the kdm and dpkg-reconfigure. But the problem still exist.
 
Now I see, that the console is not stucking at check battery state  message , rather its going to the tty1 and asking for the  login/password.

```
lspci | grep  VGA
``` shows
 
  ```

 $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

```

```
lshw -C display
``` shows
  ```

 sudo lshw -C display

  *-display
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:50300000-5037ffff ioport:2130(size=8) memory:40000000-4fffffff(prefetchable) memory:50200000-502fffff

```
My xorg.conf display section shows:
  ```

 Section "Device"
        Identifier      "Intel Corporation Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "VA1912w-4"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "VA1912w-4"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
Now, I don't have Nvidia graphics card installed, so can I safely remove whatever lists in Synaptic searching with 'Nvidia*' ?

2.  I want to stop the notification/system sound for application, e.g. while closing a button in griffith or closing a window in pidgin the system emits a sound, I want to stop all these sounds, how to do that?

3. In kde3, I can search file under the present directory using konqueror, now I see konqueror has a search bar, but that is for web, not in the local file system. I am missing this very helpful feature of konqueror, can I somehow brought it back?

4. This issue is not 9.10 specific but faced in 7.10 .. 
 Whenever I try to play an **audio cd** the system just freezes. The only in error dmesg is 
```

[    1.481899] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb

```I don't know if that helps at all.

thanks.

---

### Post by sinfaut on 2010-08-14
Oh, another thing I forgot to mention, even after entering correctly in the /etc/fstab my usb drives (pen drive and nokia phone) are showing  twice in the 'Device notifier' widget (or whatever else, I am not too sure whether this notifier is a widget or not). And one of the icon is 'mounted', the other is not.

---

