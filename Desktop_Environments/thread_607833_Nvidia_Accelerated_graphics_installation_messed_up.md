---
title: "Nvidia Accelerated graphics installation messed up."
date: 2007-11-09
forum: Desktop Environments
---

### Post by TerabyteUK on 2007-11-09
Hi,
I have an nvidia 8800.
Went to install the Accelerated graphics card though the gui on the control panel.
Said "reboot to finish" installation, or words to that effect.

When the system booted back up, I got an error message saying that the Xserver could not be started, in a blue screen.

Is this a common problem, I can boot into windows on the same machine and have a program which lets me view the linux partition. The error message said something about a log file, if you need the log file to give help, I can provide it if you tell me which directory to fetch it from.

Thanks

---

### Post by Fire_Chief on 2007-11-09
Please specify which model 8800 you have. The 8800GT is brand spankin' new and not supported by the linux drivers yet.

You may want to try using Envy```
sudo apt-get install envy
sudo envy -t
```

---

### Post by TerabyteUK on 2007-11-09
8800 Gts

---

### Post by TerabyteUK on 2007-11-11
Tried it in recovery mode, was logged in as root.

"could not find package envy."

on the first command.

---

### Post by Fire_Chief on 2007-11-11
From recovery mode, edit the file /boot/grub/menu.lst and remove the options **quiet** and **splash**. Save the file and reboot into normal mode. It should get you to a desktop using the VESA driver at which point you should be able to run the commands to install and run Envy.

---

