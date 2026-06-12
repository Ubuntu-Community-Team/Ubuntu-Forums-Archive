---
title: "dell studio 1555 - no sound 9.04"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TooDR on 2009-04-27
i just installed ubuntu 9.04 x64 on my new dell studio 1555. Problem is I have no sound whatsoever. i tried going through the no sound trouble shooting page but to no avail. Any suggestions on debugging?

[HTML]https://wiki.ubuntu.com/DebuggingSoundProblems[/HTML]

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gman@GORDON:~$ 



```

```
$ lspci -m
00:00.0 "Host bridge" "Intel Corporation" "Mobile 4 Series Chipset Memory Controller Hub" -r07 "Dell" "Device 02be"
00:01.0 "PCI bridge" "Intel Corporation" "Mobile 4 Series Chipset PCI Express Graphics Port" -r07 "" ""
00:1a.0 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #4" -r03 "Dell" "Device 02be"
00:1a.1 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #5" -r03 "Dell" "Device 02be"
00:1a.2 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #6" -r03 "Dell" "Device 02be"
00:1a.7 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB2 EHCI Controller #2" -r03 -p20 "Dell" "Device 02be"
00:1b.0 "Audio device" "Intel Corporation" "82801I (ICH9 Family) HD Audio Controller" -r03 "Dell" "Device 02be"
00:1c.0 "PCI bridge" "Intel Corporation" "82801I (ICH9 Family) PCI Express Port 1" -r03 "" ""
00:1c.1 "PCI bridge" "Intel Corporation" "82801I (ICH9 Family) PCI Express Port 2" -r03 "" ""
00:1c.3 "PCI bridge" "Intel Corporation" "82801I (ICH9 Family) PCI Express Port 4" -r03 "" ""
00:1c.5 "PCI bridge" "Intel Corporation" "82801I (ICH9 Family) PCI Express Port 6" -r03 "" ""
00:1d.0 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #1" -r03 "Dell" "Device 02be"
00:1d.1 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #2" -r03 "Dell" "Device 02be"
00:1d.2 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB UHCI Controller #3" -r03 "Dell" "Device 02be"
00:1d.7 "USB Controller" "Intel Corporation" "82801I (ICH9 Family) USB2 EHCI Controller #1" -r03 -p20 "Dell" "Device 02be"
00:1e.0 "PCI bridge" "Intel Corporation" "82801 Mobile PCI Bridge" -r93 -p01 "" ""
00:1f.0 "ISA bridge" "Intel Corporation" "ICH9M LPC Interface Controller" -r03 "Dell" "Device 02be"
00:1f.2 "SATA controller" "Intel Corporation" "ICH9M/M-E SATA AHCI Controller" -r03 -p01 "Dell" "Device 02be"
00:1f.3 "SMBus" "Intel Corporation" "82801I (ICH9 Family) SMBus Controller" -r03 "Dell" "Device 02be"
01:00.0 "VGA compatible controller" "ATI Technologies Inc" "M92 [Mobility Radeon HD 4500 Series]" "Dell" "Device 02be"
01:00.1 "Audio device" "ATI Technologies Inc" "R700 Audio Device [Radeon HD 4000 Series]" "Dell" "Device 02be"
04:00.0 "Network controller" "Intel Corporation" "Wireless WiFi Link 5100" "Intel Corporation" "Device 1321"
08:00.0 "Ethernet controller" "Broadcom Corporation" "NetLink BCM5784M Gigabit Ethernet PCIe" -r10 "Dell" "Device 02be"
09:01.0 "FireWire (IEEE 1394)" "Ricoh Co Ltd" "R5C832 IEEE 1394 Controller" -r05 -p10 "Dell" "Device 02be"
09:01.1 "SD Host controller" "Ricoh Co Ltd" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter" -r22 -p01 "Dell" "Device 02be"
09:01.2 "System peripheral" "Ricoh Co Ltd" "R5C592 Memory Stick Bus Host Adapter" -r12 "Dell" "Device 02be"
09:01.3 "System peripheral" "Ricoh Co Ltd" "xD-Picture Card Controller" -r12 "Dell" "Device 02be"

```

i ran the alsa-info script. Results: [HTML]http://www.alsa-project.org/db/?f=d2fd119abf4090eefa3bf315f5e8b9d8196c7b50[/HTML]


thanks for your help

---

### Post by TooDR on 2009-04-28
bump + update

i downloaded ubuntu x64 desktop 8.10 iso and started a live session. the sound works fine. so i believe there is a bug in the new sound drivers. :\

any ideas?

---

### Post by joseinbaraj on 2009-04-28
I am having also having the similiar motherboard and inbuilt sound card....

when i used the ubuntu 8.10 version i could get the sound only in the login screen...

in ubuntu 9.04 event the sound in the login screen disappeared...

---

### Post by snookies on 2009-05-03
I lost my sound completely after I had to reload 8.04. I have a Dell Insirion 530. I have the same Intel sound card you have. Apaarently I do not have any sound drivers nor do I have an icon.

---

### Post by jonaz on 2009-05-29
Bump, I had the same problems on 9.04 32bit

---

### Post by chammer on 2009-05-30
i posted this in another thread just a moment ago, but since i had the same problem of no sound and a lot of searches for idt sound help, i was able to get my issue resolved very easily with a single line added to the alsa modprobe script:

> 
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

```

chris@hiroshi:~$ cat /proc/asound/card0/codec#0|grep -i codec
Codec: IDT 92HD73C1X5

```

it took me a bit to find it, but i found it on [http://www.linlap.com/wiki/dell+studio+17](http://www.linlap.com/wiki/dell+studio+17) which also links back to [http://ubuntuforums.org/showthread.php?p=6543839](http://ubuntuforums.org/showthread.php?p=6543839)

basically you need to add

```

options snd-hda-intel model=dell-m6 

```

...to the end of your /etc/modprobe.d/alsa-base file.


i hope this helps!

---

### Post by byakugan on 2009-06-07
hola tengo el mismo problema con mi dell studio 
arriba escribieron la solucion pero lastima soy nuevo 
en esto de linux 

alguien puede poner la solucion paso 
por paso please

gracias

---

### Post by theBlueNibble on 2009-06-16
> **chammer said:**
> i posted this in another thread just a moment ago, but since i had the same problem of no sound and a lot of searches for idt sound help, i was able to get my issue resolved very easily with a single line added to the alsa modprobe script:



i hope this helps!


I have a CREATIVE Sound Blaster(R) X-Fi MB. I added the same line to the end of the modprobe script but the sound coming out of the in built speakers is very low. Do you think i should change anything?

---

### Post by greenie9 on 2009-06-16
> **theBlueNibble said:**
> I have a CREATIVE Sound Blaster(R) X-Fi MB. I added the same line to the end of the modprobe script but the sound coming out of the in built speakers is very low. Do you think i should change anything?

yup, i have the same quirk as well...
(other fixes/issues in sig)

---

### Post by mynameinc on 2009-06-18
> **byakugan said:**
> hola tengo el mismo problema con mi dell studio 
arriba escribieron la solucion pero lastima soy nuevo 
en esto de linux 

alguien puede poner la solucion paso 
por paso please

gracias

Translated:
> **byakugan said:**
> Hi, I have the same problem with my Dell Studio.
The solution has been written, but "this Linux" (presumably 9.04) has caused me problems.

Can someone please put the solution step by step?

Thanks.

---

### Post by mynameinc on 2009-06-18
If anyone has a solution, please use Google Translate or another tool so byakugan;7414143 can read it.

---

### Post by Pabloo0o0 on 2009-06-20
> **byakugan said:**
> hola tengo el mismo problema con mi dell studio 
arriba escribieron la solucion pero lastima soy nuevo 
en esto de linux 

alguien puede poner la solucion paso 
por paso please

gracias


Holas, es muy simple. 

Abre la consola y pone el siguiente linea

```
cat /proc/asound/card0/codec#0|grep -i codec
```y si el resultado es Codec: IDT 92HD73C1X5

vamos bien, ahora escribe lo siguiente en la consola
```
 sudo gedit /etc/modprobe.d/alsa-base.conf
```Ahi te va preguntar la password de superusuario

Despues al final del texto agregas la siguiente linea

```
options snd-hda-intel model=dell-m6
```
Guardas la config y despues reinicias el ubuntu y listo...
Espero q te resulte..):P

---

### Post by MauveForest on 2009-06-21
I have been having the same problem with my dell as well. (same model). I am completely new to Linux and Ubuntu both so I have been having difficultly with using the command terminal and such, not knowing exactly how to fix things. I have been following the  instructions in this thread, but it doesn't seem to be working for me. 
```
options snd-hda-intel model=dell-m6
```

I use this in the command terminal and

```
bash: options: command not found
```

comes up. I assume this means the command isn't the correct one? Or am I missing steps to this? Thanks if you can help me.

---

### Post by bensh_ on 2009-06-24
> **chammer said:**
> 
i hope this helps!

Chammer, thanks a lot!

Just adding this line of configuration option 
```

options snd-hda-intel model=dell-m6

```

to File 
```
/etc/modprobe.d/alsa-base.conf
```
helps!

Got Sound now using Ubuntu 9.04 on DELL Studio 15 (1555)!

---

### Post by Clifton McIntosh on 2009-07-28
> **bensh_ said:**
> Chammer, thanks a lot!

Just adding this line of configuration option 
```

options snd-hda-intel model=dell-m6

```

to File 
```
/etc/modprobe.d/alsa-base.conf
```
helps!

Got Sound now using Ubuntu 9.04 on DELL Studio 15 (1555)!
This also worked for me with a Studio 1555 and Ubuntu 9.04.

---

### Post by beauwalnut on 2009-07-31
I am really new to unbuntu but these are the steps that got my 1555 going.

ok step 1 : go to 
places>computer>filesystem>etc>modprobe.d>alsa-base.conf

step 2: open alsa-base.conf and paste in the code below at the bottom of the page. 
     Code:
     options snd-hda-intel model=dell-m6 
Step 3: save changes and restart.

IF you dont have permission to change the file do this:
System > Administration > Login Window
Under "Security" tab check the box beside the line "Allow local system administrator login"

log in as "root" and repeat the steps above.

---

### Post by basimkhalid on 2009-08-05
Hi All,
 
Does this (adding "options snd-hda-intel model=dell-m6 ") to conf file helps in creative Xi-Fi also or is it applicable only for the default sound driver (I think it is intel) for 1555?

---

### Post by johnrobert on 2010-02-14
Chammer, thank you! That worked perfectly for my new Studio 15. You rock. :P

---

### Post by mellowtothemax on 2010-05-13
Never ever ever log in as root or allow root as a login unless you know exactly what you are doing.  Big security risk.

Either use the command 'sudo gedit /etc/modprobe.d/alsa-base.conf' or 'gksu gedit /etc/modprobe.d/alsa-base.conf' from either the terminal or from the run command Alt+F2.

You can also install Ubuntu-Tweak and enable administrator extension to nautilus to open folders and files with full permissions.

---

