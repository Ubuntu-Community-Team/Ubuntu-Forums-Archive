---
title: "Conky with MSI Geforce GTX-760 (Nvidia)"
date: 2015-05-07
forum: Desktop Environments
---

### Post by ahulshof on 2015-05-07
Motherboard: MSI H97M-E35
Graphics card: MSI Geforce GTX-760 (Nvidia)

how can I get the readings of this graphics card and how do i get the readings for hardrive and motherboard? I.e. fanspeeds and temperatures?

---

### Post by CantankRus on 2015-05-08
For the nvidia card, if it is suppoted by the nvidia driver, you can use for the temp
```
nvidia-settings -t -q GPUCoreTemp
```
If you installed **conky-all**, the inbuilt nvidia variable will be available.
From man conky....
> **nvidia** threshold temp ambient gpufreq memfreq imagequality
[INDENT]Nvidia graficcard support for the XNVCtrl library. Each option can be shortened to the least significant part. Temperatures are printed as float, all other values as integer.
threshold The thresholdtemperature at which the gpu slows down 
temp Gives the gpu current temperature 
ambient Gives current air temperature near GPU case 
gpufreq Gives the current gpu frequency 
memfreq Gives the current mem frequency 
imagequality Which imagequality should be chosen by OpenGL applications[/INDENT]

For hard drive temps install and configure **hddtemp**
For fan speeds and cpu temp install and configure **lm-sensors**
The results you get from lm-sensors depends on how well your motherboard is supported.
See [**_[COLOR="#B22222"]THIS POST[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&p=12700126#post12700126")

If you need further help, install inxi (sys info script)
```
sudo apt-get install inxi
```
and post the output of 
```
inxi -b
```

eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] inxi -b**
System:    Host: Trusty Kernel: 3.16.0-37-generic x86_64 (64 bit) Desktop: Unity 7.2.4
           Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x Bios: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.9hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 1250.3GB (11.6% used)
Info:      Processes: 257 Uptime: 1:54 Memory: 1946.4/3934.9MB Client: Shell (bash) inxi: 2.2.19
```

---

### Post by ahulshof on 2015-05-08
If I so that I get following output:
@server1:~$ nvidia-settings -t -q GPUCoreTemp
44
44

how can I get only 1 temp reading. now my result in conky is:   44                     44

---

### Post by CantankRus on 2015-05-08
Use...```
nvidia-settings -t -q GPUCoreTemp | head -n1
```

---

### Post by ahulshof on 2015-05-08
got a problem. Gedit crashed while I was cofiguring conky.
Now my .conkyrc file shows strange characters:

TEXT
${font Droid Sans:style=Bold:size=8}Ð¡Ð˜Ð¡Ð¢Ð•ÐœÐ $stippled_hr${font}

any idea how I can fix this?

---

### Post by CantankRus on 2015-05-08
Does it just show strange characters for that one file?
In your file browser show hidden files and check if gedit made a backup.
It will be the same name but ending in a "~"

---

### Post by ahulshof on 2015-05-08
yes it did make a conkyrc~
Can I recover this?

---

### Post by CantankRus on 2015-05-08
You can view "~" files by drag and dropping them into an open gedit window.
If the "~" file looks ok, close gedit  and delete your current file or rename by just adding **.bak** to the end.
eg **.conkyrc.bak**
and then rename your gedit backup file by just removing the trailing "~"

---

