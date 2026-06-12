---
title: "2 vid cards conflicting... install help pls"
date: 2005-10-15
forum: Desktop Environments
---

### Post by BlingFree on 2005-10-15
I tried to install Ubuntu and it died when it came time to start the gui... at first I thought it was due to no support for 3dfx voodoo3 but I was wrong... 

So I gave up adn tried installing a different distro Mandriva 2006... when it came to verifying the vid driver if said it was configured for the onboard vid (intel i830 i think)... that was obviously wrong so I changed it to my voodoo3 and all was well.

It got me to thinking that the same mistake was happening in the Ubuntu install... it was trying to install my onboard vid (tho its disabled and I'm running through the voodoo3)

So...

Is there a way to fix this during the Ubuntu install? To make sure that its installing the voodoo driver and not the Intel driver? 

Any help would be much appreciated.

---

### Post by BlingFree on 2005-10-16
ok... if nto then is there a way to change vid drivers after booting into the secure mode?

any help would be lovely.

---

### Post by az on 2005-10-16
Sure.  Boot into recovery mode and run
dpkg-reconfigure xserver-xorg 

and enter the driver by hand.  Make sure you use the correct device, too ...

Ex: 00.08.00 (do lspci to help you out)

---

### Post by BlingFree on 2005-10-16
awesome man... thank you for sending me in the right direction

I'm a fan of google adn I'm looking now but... perhaps you could help and explain what you mean by :enter teh driver by hand"

are there soem specific values I have to enter?

again, I'll search but any help is always apprecaited :D

THansk again man!

---

### Post by BlingFree on 2005-10-16
ok... so i got into lspci and it gave me the following

0000:01:0b.0 3dfx Voodoo3 (and other stuff)

but when I try to put that value in the PCI address field while doing the reconfig it says thats not the right value....yikes!

any clues?

---

### Post by az on 2005-10-16
Doe it tell you that it is detecting two cards?  If not, take the default pci listing and see what happens using the 3dfx driver name.

---

### Post by BlingFree on 2005-10-16
well it seems to have went over my head... 

is lspci the only way to get the correct value for the PCI card? (ex 00:08.00)?

or is there another way to find out correctly? 

sorry for the newbness... i'm not used to feeling helpless like this :(

thanks again for all your help!

---

### Post by BlingFree on 2005-10-16
does the example 00:08:00 relate to bus:device:function?

---

### Post by az on 2005-10-16
[QUOTE=BlingFree]well it seems to have went over my head... 

is lspci the only way to get the correct value for the PCI card? (ex 00:08.00)?

or is there another way to find out correctly? 

![/QUOTE]
If there is no X session running, dpkg-reconfigure xserver-xorg should pick it up by itself.  If it detects two devices it should ask you about that.

---

### Post by BlingFree on 2005-10-16
on autodetect it picks up my onboard vid and proceeds to try to install that... it doesnt mention the voodoo3 at all from what I can see... sorry for the delayed responses but I have to keep rebooting to mess with linux... then hop back on windows to get back online...

---

### Post by az on 2005-10-16
Can you post the output of lspci?

lspci > file
and then copy that file to a usb drive or a fat32 partition? 

sudo mount /dev/sda1 /mnt
sudo cp file  /mnt/


Also, show the output of lsmod, too.

---

### Post by BlingFree on 2005-10-17
i am a failure... what can I say??

I got lspci and lsmod into files but i have no fat32 HD or partition... adn failed to even cleanly mount my floppy drive... 

I'll just have to work with the advice youve given me so far... maybe I can figure sumthin out in the meantime.

Thank you.

---

### Post by BlingFree on 2005-10-17
well... i did it... using ext2ifs in XP... whew... so heres the info...

lspci output
```

0000:00:00.0 Host bridge: Intel Corp. 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
0000:01:0d.0 USB Controller: NEC Corporation USB (rev 43)
0000:01:0d.1 USB Controller: NEC Corporation USB (rev 43)
0000:01:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:01:0e.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```

lsmod output
```

Module                  Size  Used by
ntfs                   92016  0 
snd_mpu401              6344  0 
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
analog                 10528  0 
gameport               14472  1 analog
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
ibmcam                 43884  0 
usbvideo               24836  1 ibmcam
videodev                9344  1 usbvideo
snd_intel8x0           30144  0 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
hw_random               5268  0 
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
intel_agp              21276  1 
agpgart                32328  1 intel_agp
dm_mod                 50364  1 
tsdev                   7616  0 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  0 
parport_pc             31812  0 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
tulip                  45088  0 
ehci_hcd               29448  0 
ohci_hcd               18564  0 
uhci_hcd               28048  0 
usbcore               104188  6 ibmcam,usbvideo,ehci_hcd,ohci_hcd,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  4 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  2 
fbcon                  34176  0 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0 
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0 
commoncap               6784  1 capability

```

---

### Post by az on 2005-10-17
I dunno.

If there is no bug report about this yet, perhaps you should file one...

[https://launchpad.net/malone/distros/ubuntu](https://launchpad.net/malone/distros/ubuntu)

[https://launchpad.net/malone/bugs/+package](https://launchpad.net/malone/bugs/+package)

---

### Post by BlingFree on 2005-10-17
so I'm assuming that none of the above helps to fill in the xx:xx:xx value that xserver-xorg wants?

---

### Post by BlingFree on 2005-10-18
for the record Kubuntu does it too... dunno why it wouldnt... guess i'm just optimistic...

as far as bug reports go... I'm not really sure what I'd report... 

The fact that the installer only wants to install the onboard vid?
or
when I try to enter what lspci tells me is my info that xserver-xorg needs that it says invalid?

i dunno... i gots issues!!

---

### Post by BlingFree on 2005-10-19
gotta love google... I found a few examples online of voodoo3 people's xorg.conf

all is well now...

btw I got my xx:xx:xx value from looking in win xp's device properties... lovely eh?

---

### Post by BlingFree on 2005-10-21
Just wanted to thank you for all your assistance.

Very much appreciated. I'm on my way to being a full time Ubuntu linux user.

Thanks again.

---

