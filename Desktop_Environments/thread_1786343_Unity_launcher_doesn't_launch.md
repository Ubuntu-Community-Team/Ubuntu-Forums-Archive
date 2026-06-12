---
title: "Unity launcher doesn't launch"
date: 2011-06-19
forum: Desktop Environments
---

### Post by RikoW on 2011-06-19
Dear all,

I just upgraded to Natty this weekend, so don't have much experience with Unity yet. I tried to create a launcher, which starts an application on a VMware virtual machine using vmware-unity-helper (lot's of unity here :).

Anyway, so I created the launcher, e.g. MS Project:

```
> cat MS\ Project\ 2007\ Pro\ VM.desktop 
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=x-vmware-564d30e807cd38d7-86130670192a99ac-Microsoft-Project-Professional
Name[en_US]=MS Project 2007 Pro VM
Comment[en_US]=start MSPE4XFEL on VM
Exec=/home/wichmann/bin/VMstartApp WINPROJ.EXE
Name=MS Project 2007 Pro VM
Comment=start MSPE4XFEL on VM
Icon=x-vmware-564d30e807cd38d7-86130670192a99ac-Microsoft-Project-Professional

```

The Exec command is just a little python script, which checks whether the VM is running and then executes the vmware-unity-helper command with the correct path and all.

The launcher works, when I double-click in in nautilus. But when I drag'n'drop to the unity bar and click it nothing happens. I pulses some (as if the application would start) but nothing happens.

Any ideas?

Thanks,
           Riko

---

### Post by wildmanne39 on 2011-06-20
> **RikoW said:**
> Dear all,

I just upgraded to Natty this weekend, so don't have much experience with Unity yet. I tried to create a launcher, which starts an application on a VMware virtual machine using vmware-unity-helper (lot's of unity here :).

Anyway, so I created the launcher, e.g. MS Project:

```
> cat MS\ Project\ 2007\ Pro\ VM.desktop 
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=x-vmware-564d30e807cd38d7-86130670192a99ac-Microsoft-Project-Professional
Name[en_US]=MS Project 2007 Pro VM
Comment[en_US]=start MSPE4XFEL on VM
Exec=/home/wichmann/bin/VMstartApp WINPROJ.EXE
Name=MS Project 2007 Pro VM
Comment=start MSPE4XFEL on VM
Icon=x-vmware-564d30e807cd38d7-86130670192a99ac-Microsoft-Project-Professional

```

The Exec command is just a little python script, which checks whether the VM is running and then executes the vmware-unity-helper command with the correct path and all.

The launcher works, when I double-click in in nautilus. But when I drag'n'drop to the unity bar and click it nothing happens. I pulses some (as if the application would start) but nothing happens.

Any ideas?

Thanks,
           RikoHi, look in my signature it say power users guide for natty, click on it and go down to launchers and it will tell you how to make launchers for natty.

---

