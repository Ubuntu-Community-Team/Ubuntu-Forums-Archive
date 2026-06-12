---
title: "How can you view your specs in Ubuntu?"
date: 2009-02-16
forum: General Help
---

### Post by Vic the Trader on 2009-02-16
I believe in Windows it's right click 'my computer', go to 'properties'.  How can you get that same information in Ubuntu 8.10?

---

### Post by Phlee on 2009-02-16
What kind of "Specs" are you looking for?

---

### Post by howefield on 2009-02-16
Open a terminal and type

```
lshw
```

Or a thousand other commands depending on what/how you want the info, eg., lspci or lsusb etc.

---

### Post by mb_webguy on 2009-02-16
You can open System Monitor on the System->Administration menu and click on the System tab.  This will show you your Linux kernel version, Gnome version, processor(s), and memory.

You can use numerous terminal commands for more detailed information.  Or you can install sysinfo (either in Add/Remove Applications, Synaptic, or with "sudo apt-get install sysinfo" in the terminal) which gives you a huge amount of information in a GUI interface.  Once you install it, you can find it under Applications->System Tools.

---

### Post by stchman on 2009-02-16
> **Vic the Trader said:**
> I believe in Windows it's right click 'my computer', go to 'properties'.  How can you get that same information in Ubuntu 8.10?

Install the package sysinfo.

```

sudo apt-get install sysinfo

```

It will be found under Applications--->System Tools

It will give you all the stats of your system from a hardware perspective.  Also run the System Monitor as it depicts CPU, RAM, and Network usage.

---

### Post by Vic the Trader on 2009-02-16
The sysinfo program is pretty nice, and I like how a the 'system tools' section was created under applications after installation.
I installed the Gnome Partition Editor and it didn't appear under applications.  Where can I find that using the GUI?

---

### Post by mb_webguy on 2009-02-16
It's under System->Administration as Partition Editor.

---

### Post by Vic the Trader on 2009-02-16
Much obliged.

---

### Post by Saija on 2009-02-16
thank you stchman & howefield for the command & application to show the system properties, i think i'll try to know the many ls's commands, i knew the always helpful ls and lsof, but that lshw is very informative... ;)

---

### Post by oldos2er on 2009-02-16
lspci, lsusb, etc.

---

### Post by linux_tech on 2009-02-16
Some commands to gather various information:
```

lshw 
uname -a 
lspci 
free -m
df -h
lsmod | head
htop
cat /proc/cpuinfo
sudo dmidecode

```

---

