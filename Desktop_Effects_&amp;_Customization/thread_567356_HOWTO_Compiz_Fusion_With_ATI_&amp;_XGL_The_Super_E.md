---
title: "HOWTO: Compiz Fusion With ATI &amp; XGL The Super Easy Way"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by dje on 2007-10-04
[size="7"]**Project not continued**[/size]

---

### Post by Moozie on 2007-10-04
> **dje said:**
> If you have a ATI graphics card and you want Compiz Fusion on Feisty Fawn, try my fully automatic installer script to get you set up in minutes! To download and try it simply go to the red link in my signature. 

Enjoy and post any comments, questions and ideas here :)

dje

I Clicked the link in your sig, it didn't work and now I don't even have the menu for desktop effects and that sux.

Do you have a fix?

---

### Post by Rupertronco on 2007-10-05
Moozie what version of ubuntu are you using? If you're using gutsy, it won't work.

---

### Post by amadeus266 on 2007-10-05
dje, you also need to explain which ati cards your script is for. Will it work on the same cards that use the default ubuntu drivers or only on cards that require the proprietary drivers? (i.e. 9500 and up)

---

### Post by dje on 2007-10-05
It says in the Readme how to test your card, which my website tells you to read before using the script. I have tested it many times with a 256MB ATI Radeon Xpress 1150 HyperMemory card. Moozie: did you login to th xgl session and run 'compiz --replace'? To get the settings manager try running 'ccsm', both without the quotes. I'm sorry if you are experienceing difficulty, ofcourse you can take a look at the code to see if you can see a problem. Original post updated about the cards.

---

### Post by Moozie on 2007-10-05
it said something about searching for the packages using the broken filter

---

### Post by dje on 2007-10-05
Moozie: Is that when you try to install it? If so i don't think i can help you because it sounds like something is wrong with the actual compiz packages not my installer, all it does is do a sudo apt-get install so, have a look at the code to check (right click open in text editor). Could you also post the contents of the two other files that came with the installer (startxgl.sh, in /usr/local/bin, and xgl.desktop, in /usr/share/xsessions) to check there are no problems there. All i can say is i have tested it using the card i added to the original post with the propietary driver and it works fine.

EDIT: The desktop effects menu is supposed to go, it is replaced by ccsm which is Compiz Config Settings Manager. Also do you use ubuntu because it only works on ubuntu with gnome (not kubuntu or xubuntu or any derivatives, that i know of), it does state this in the readme. What version of ubuntu do you use and what graphics card do you have, use the command in the readme to check it and post the output here.

---

### Post by Moozie on 2007-10-05
> **Rupertronco said:**
> Moozie what version of ubuntu are you using? If you're using gutsy, it won't work.
Fiesty... Do you have a fix?

---

### Post by dje on 2007-10-05
Please read the above post, i have never come across your problem. Please answer the questions in the post above and then i can hopefully help you :)

---

### Post by Moozie on 2007-10-05
> **dje said:**
> 

EDIT: The desktop effects menu is supposed to go, it is replaced by ccsm which is Compiz Config Settings Manager. Also do you use ubuntu because it only works on ubuntu with gnome (not kubuntu or xubuntu or any derivatives, that i know of), it does state this in the readme. What version of ubuntu do you use and what graphics card do you have, use the command in the readme to check it and post the output here.

The CCSM is there but nothing works.. I Use Ubuntu Fiesty Fawn... How would I find out what graphics card I have?

---

### Post by dje on 2007-10-05
```
fglrxinfo
```
then please post the output here, please also answer the other questions ;)

---

### Post by Moozie on 2007-10-05
When I go to the Restricted Drivers Manager it tells me "Your Hardware does not need any Restrited Drives"

---

### Post by Moozie on 2007-10-05
> **dje said:**
> ```
fglrxinfo
```
then please post the output here, please also answer the other questions ;)


Where do I type that in?

---

### Post by dje on 2007-10-05
sorry, go to applications >> accesories >> terminal and type it in and hit return!

---

### Post by Moozie on 2007-10-05
> **Moozie said:**
> Where do I type that in?
This is what the terminal thing told me... (attached image)

---

### Post by dje on 2007-10-05
I'm no expert but i believe that means your graphics driver is not installed, without that you will get no compiz fusion. An example of what you should get is in the readme file

---

### Post by Moozie on 2007-10-05
If I didn't have a graphics driver wouldn't that mean there wouldn't be an image on the screen?
....

Evidently if I understood what your readme file said I wouldn't have tried to install it... Do you have a fix or the next thing I need to do to either make it work or get it back to normal?

---

### Post by dje on 2007-10-05
What card do you have? I am no expert again but i think that to have all the fancy 3d effects you need to have another driver, to get mine i went to restricted drivers manager. But again, what card do you have?

EDIT: The driver i installed is called the ATI accelerated graphics driver so i guess that means it enables 3d acceleration? without an accelerated graphics driver i dont think you will get compiz fusion working.

---

### Post by Moozie on 2007-10-05
how do I find what card I have?

---

### Post by dje on 2007-10-05
In a terminal do:
```
lspci
```
and then post the output here. Also what computer is it?

---

### Post by Moozie on 2007-10-05
> **dje said:**
> In a terminal do:
```
lspci
```
and then post the output here. Also what computer is it?

Dell Optiplex 260

(Screenshot)

---

### Post by dje on 2007-10-05
Could you also do:
```
lshw
```
and post the output

---

### Post by dje on 2007-10-05
I HAVE FOUND YOU PROBLEM:
You have a intel graphics card, this guide is for ATI graphics cards. Unlucky but i'm sure there are other guides/scripts for intel cards out there. Thankyou for giving my script a go though :)

---

### Post by Moozie on 2007-10-05
> **dje said:**
> Could you also do:
```
lshw
```
and post the output

timothy@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1130MB
     *-cpu
          product: Intel(R) Celeron(R) CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.3
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f0000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 01
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0
             resources: iomemory:e8000000-efffffff iomemory:ff680000-ff6fffff irq:16
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: Generic USB Hub
                   vendor: ALCOR
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.12
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb
                      description: Mass storage device
                      product: Flash Disk
                      vendor: USB
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 2.00
                      serial: AA00700063934203
                      capabilities: usb-2.00 scsi
                      configuration: driver=usb-storage maxpower=200mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff40-ff5f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffa00800-ffa00bff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@01:0c.0
                logical name: eth0
                version: 02
                serial: 00:08:74:b4:d2:76
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A ip=192.168.1.101 latency=64 mingnt=255 multicast=yes
                resources: iomemory:ff8e0000-ff8fffff ioport:ecc0-ecff irq:18
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:ffa0-ffaf iomemory:50000000-500003ff irq:18
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dc80-dc9f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc40-dc7f iomemory:ffa00400-ffa005ff iomemory:ffa00000-ffa000ff irq:20
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by dje on 2007-10-05
Yes I Have Found Your Problem, Please See My Last Post :)

---

### Post by Moozie on 2007-10-05
> **dje said:**
> I HAVE FOUND YOU PROBLEM:
You have a intel graphics card, this guide is for ATI graphics cards. Unlucky but i'm sure there are other guides/scripts for intel cards out there. Thankyou for giving my script a go though :)

Ok so how do I get rid of your script so it will ATLEAST go back to the way it was before?

---

### Post by dje on 2007-10-05
It depends, do you want to keep compiz fusion installed? Do you want to keep the xgl session and do you want to keep the repositories my script added?

---

### Post by Moozie on 2007-10-05
I want it all to work, is there a way for me to get all of this to work?

What is the "XGL Session"?



EDIT::
I gotta go take care of some stuff.. back in about an hour.

---

### Post by dje on 2007-10-05
Again im no expert but i believe you don't need the xgl session  with an intel graphics card to run compiz fusion (you may want to start a new thread to check this). So in a terminal do (one line at a time)
```
sudo apt-get -y remove xserver-xgl
sudo rm startxgl.sh /usr/local/bin
sudo rm xgl.desktop /usr/share/xsessions
```

This will remove xgl (which i believe you dont need, but like i said you may want to start a new thread to check this). So this will leave compiz fusion installed and ready to go if you get your accelerated graphics driver (search or start a new thread for this also, perhaps). Again thankyou for trying my script and i hope i have been of some help to you when it did not work :)

dje

---

### Post by dynamethod on 2007-10-05
i have an ATI X800XT AGPx8 card, heres my fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6747 (8.40.4)

ive completely removed compiz and all the other compiz related things in synaptic, 

is your script compatible with my card?

---

### Post by dje on 2007-10-05
I think it will work but of course, i cant be 100% sure i have only tested it with the card stated in the original post. PLEASE READ THE README BEFORE USING THE SCRIPT. Please post on whether it works for you. Happy installing :)

---

### Post by dynamethod on 2007-10-05
does not work for ATI X800 XT cards sorry

xgl makes a total mess of everything, ie: you cant see nothing

---

### Post by dje on 2007-10-05
Sorry

Look here for a guide I based the script on [http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html]("http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html")
See if that works, it could be a bug in my script :(

---

### Post by dje on 2007-10-05
I Believe There Is A Bug In My Script, It Is Offline At The Moment

---

### Post by dynamethod on 2007-10-05
ah sorry ignore this post my mistake, i dont thinks its your script thats the problem, i think there just a problem with xgl and ati X800 cards myself, i could be wrong but im pretty certain its xgl related

---

### Post by dje on 2007-10-05
What did? xgl?

This will remove xgl:

sudo apt-get -y remove xserver-xgl
sudo rm startxgl.sh /usr/local/bin
sudo rm xgl.desktop /usr/share/xsessions

dynamethod: in that case ignore the pm i sent you, i will take the scripts offline and make sure they work properly before putting them online again. Thank you for being brave and giving it a go :)

---

### Post by dynamethod on 2007-10-05
no problem, but again, i dont think its your script thats the problem, its xgl and some ATI cards, they dont like each other :S

---

### Post by Moozie on 2007-10-05
Removing XGL Didn't help... What do I do to get everything back to the way it was?

---

### Post by dje on 2007-10-06
Moozie do this:
```
sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```
and then:
```
sudo apt-get install compiz-core desktop-effects
```
and then:
```
sudo gedit /etc/apt/sources.list
```
and delete the following:
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

then save and close the file

That should undo my script and bring back your desktop effects menu item

---

