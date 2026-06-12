---
title: "Unable to install Red Hat ."
date: 2008-06-12
forum: Fedora/RedHat and derivatives
---

### Post by rraj.be on 2008-06-12
Hello geek's

This is my pc configuration.

```
pentium dual core processor [3.2GHz]

512 MiB DDR2 RAM

2 x 160 GiB SATA hard disk.


```

I tried to install red hat linux for several times and each time its getting me error something like no device found to install red hat.

Is it possible to install red hat in SATA hard disk[, along with above configuration.]

---

### Post by John.Michael.Kane on 2008-06-12
Not enough information is given.

What version of Red-hat? is the version Red-hat regular or one of the derivatives?

What is full spec of the machine including the sata controller make/model?

---

### Post by rraj.be on 2008-06-13
I am using intel pentium dual core processor[3.2GHz]

512 MiB DDR2 RAM.

2 x 160 GiB SATA HARD DISK.

when i tried to install red hat or fedora i am getting to the screen asking for 

```
press enter for install in graphic mode

..........

.......

text mode etc.
```

I selected graphic mode by pressing ENTER.

the screen starts to load and after a few seconds its displaying like this

```


//something goes here

.........................

...........................


...............

ACPI : Subsystem revission 20040816

ACPI : Intrepter enabled

ACPI : Using PIC for Interrupt routing

ACPI : PCI Root bridge [PC10] (00:00)

PCI : Prbing PCI hardware.
```


after this the screen remaing the same and there is no improvement beyond 
[COLOR="Black"][/COLOR]
[COLOR="Red"]Probing PCI hardware.[/COLOR]

what is the problem.

cant i install rdhat or fedora in my system.

---

### Post by Antman on 2008-06-13
Which version of Fedora?

---

### Post by rraj.be on 2008-06-13
I think its fedora core 3

---

### Post by techmarks on 2008-06-13
It's either the motherboard

DG965RY
DG965GF

or the SATA HD

read this;

[http://www.linuxquestions.org/questions/red-hat-31/red-hat-installation-and-core-2-duo-479778/]("http://www.linuxquestions.org/questions/red-hat-31/red-hat-installation-and-core-2-duo-479778/")

---

### Post by rraj.be on 2008-06-13
I know its beginers place and not for other OS discussions.

But i had posted it here because its a bit urgent for me.

So please help me.

 Unable to install Fedora core 3
I am using intel pentium dual core processor[3.2GHz]

512 MiB DDR2 RAM.

2 x 160 GiB SATA HARD DISK.

when i tried to install red hat or fedora i am getting to the screen asking for


```

press enter for install in graphic mode

..........

.......

text mode etc.
```

I selected graphic mode by pressing ENTER.

the screen starts to load and after a few seconds its displaying like this


```

//something goes here

.........................

...........................


...............

ACPI : Subsystem revission 20040816

ACPI : Intrepter enabled

ACPI : Using PIC for Interrupt routing

ACPI : PCI Root bridge [PC10] (00:00)

PCI : Probing PCI hardware.

```

after this the screen remaing the same and there is no improvement beyond

Probing PCI hardware.

what is the problem.

cant i install redhat or fedora in my system.

---

### Post by ajmorris on 2008-06-13
hi there,
at the grub boot option from the fedora cd, press 'e' on the option you choose, and edit the kernel line and put this at the end of it acpi=off:
then press 'enter' then press 'b' on you edited version to boot it.
Hopefully this works, if it doesnt, you could try something like noapic ...

AJ

---

### Post by Antman on 2008-06-13
> **rraj.be said:**
> I think its fedora core 3
Try Fedora 8, it works fine on SATA drives (at least it did on mine).

---

### Post by Cypher on 2008-06-13
FC3 is old..FC9 was recently released, any reason you aren't using a later version of FC?

---

### Post by rraj.be on 2008-06-13
I am usig FC3 because i just have that only.

I dont have any other versions of fedora core

I cant even download vecause my net is very slow

---

### Post by Joeb454 on 2008-06-13
You may want to look into this: [Fedora Free Media Program]("http://fedoraproject.org/wiki/Distribution/FreeMedia")

---

### Post by rraj.be on 2008-06-13
my board is 946GZis

Hard disk is SATA.

pci config is ```
raj@raj-workstation:~$ lspci
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
raj@raj-workstation:~$ 
```

---

### Post by Joeb454 on 2008-06-13
Like above, is it an actual Red-Hat installation you're attempting, or one of it's derivatives (Fedora etc.)

---

### Post by frodon on 2008-06-13
Duplicate thread merged.

@rraj.be, next duplicate thread you open will imply a 10 point infraction which will reduce your forum access be warned, we wasted enough time merging/closing your duplicate threads so please get the point.

---

### Post by shawnansasio on 2008-07-01
There is a way to order a free fedora cd read this: [http://fedoraproject.org/wiki/Distribution/FreeMedia](http://fedoraproject.org/wiki/Distribution/FreeMedia)

(Next Month)

---

