---
title: "Attempting to flash BIOS"
date: 2011-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MisterEverythingsWorkin on 2011-07-10
I have a Dell inspiron mini 9 and am running Ubuntu 11 off of a flash drive and am trying to flash the bios using the terminal.   I'm following this 

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

```
# set up repos wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash aptitude install firmware-addon-dell aptitude install $(bootstrap_firmware -a) update_firmware
```

I get to the aptitude install $(bootstrap_firmware -a) and keep coming up with 

```
  ubuntu@ubuntu:/$ sudo apt-get install $(bootstrap_firmware -a)
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ae-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ae
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27a6-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27a6
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27c9-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27c9
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27c8-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27c8
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27cc-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27cc
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ca-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ca
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27cb-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27cb
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2448-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2448
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27da-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27da
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d8-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d8
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ac-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27ac
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27df-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27df
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2381-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2381
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2382-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2382
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27b9-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27b9
  E: Unable to locate package pci-firmware-ven-0x14e4-dev-0x4315-subven-0x14e4-subdev-0x04b5
  E: Unable to locate package pci-firmware-ven-0x14e4-dev-0x4315
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2383-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x197b-dev-0x2383
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d4-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d4
  E: Unable to locate package pci-firmware-ven-0x10ec-dev-0x8136-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x10ec-dev-0x8136
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d0-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d2-subven-0x1028-subdev-0x02b0
  E: Unable to locate package pci-firmware-ven-0x8086-dev-0x27d2
  
```


I also tried to use FreeDOS to install the BIOS but kept getting unable to run the program type in DOS.   It was a .exe

---

### Post by An Sanct on 2011-07-11
The BIOS update, you downloaded from dell is actually a Win32 application, so a GUI unpacker and flasher.

> The  file QHA07_Win.exe is using the Hard Drive format and _is designed to be directly executed from Windows environments_.So, if you run this with wine, a "WinPlash" window appears, giving you the option to [backup and flash] and [just backup] your BIOS.

That is the way to extract the files to "c:\windows\temp\WINPLASH" (you see the exact directory in the first dialog)

note: I did not click any other buttons, since it would be risky for me, without the correct board or bios, to do so.

It would also be risky to do so *with* a correct board and bios combination under WINE, so do not do it!

---

### Post by MisterEverythingsWorkin on 2011-07-11
I tried to do that as well using Wine.  I kept getting error code 5 when I would try to do that.  If none of these options work, what am I supposed to do?   I need to update the BIOS so this netbook will stop beeping once it hits the 10% battery life left.  It's still running A01.

---

### Post by psusi on 2011-07-11
> **MisterEverythingsWorkin said:**
> I tried to do that as well using Wine.  I kept getting error code 5 when I would try to do that.  If none of these options work, what am I supposed to do?   I need to update the BIOS so this netbook will stop beeping once it hits the 10% battery life left.  It's still running A01.

You realize that letting it get that low shortens the battery life?  Best to just plug it in before it starts beeping.

---

### Post by MisterEverythingsWorkin on 2011-07-11
This may be true, but if I'm in class and the battery is running down after having it on for an hour, I'd rather it just drop below 10% without beeping.

---

### Post by An Sanct on 2011-07-11
Now, I don't know how this updater works, altho I used it on my Windows-dell machine ...

but from observing what went on, when I did, I could (maybe falsely ...) conclude, that it modifies the boot sector and then reverts it back to the original state afterwards ... counting on that, that the boot sector is MS Windows compatible and maybe breaking others ...

Anyway, Googling for an answer, I came across this: "[Ubuntu unleashed]("http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html")", this might be the way for you ... also find the appropriate "header" - HDR file, the link in that post is not working anymore...

---

### Post by leonbravo on 2011-09-04
Hi, I'm trying to upgrade my bios and firmware too, I've got similar errors...  in my laptop and a office server poweredge 2900. 

Has anyone successfully updated from dell repos?

My laptop has the following config
Linux XPS-M1330 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Messages go like these:
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2a02
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2a03-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2a03
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2850-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2850
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2815-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2815
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283e-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283e
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2829-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2829
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2849-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2849
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2448-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2448
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2845-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2845
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283f-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283f
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2841-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2841
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x4222-subven-0x8086-subdev-0x1020
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x4222
E: Unable to locate package pci-firmware-ven-0x14e4-dev-0x1713-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x14e4-dev-0x1713
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2832-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2832
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2831-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2831
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2830-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2830
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2836-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2836
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x284b-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x284b
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2a00-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2a00
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2834-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2834
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2835-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x2835
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283a-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x8086-dev-0x283a
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0592-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0592
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0852-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0852
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0832-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0832
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0822-subven-0x1028-subdev-0x0209
E: Unable to locate package pci-firmware-ven-0x1180-dev-0x0822

---

### Post by nariub on 2011-09-07
I have a USB stick with Freedos on it.
I copy the dell bios from the webpage onto the stick
boot the usb stick
run the executable.

bios updated.

---

