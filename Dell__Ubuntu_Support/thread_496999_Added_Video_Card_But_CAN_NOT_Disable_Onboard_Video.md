---
title: "Added Video Card But CAN NOT Disable Onboard Video:"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by Scotty1982 on 2007-07-09
Hi, I just wanted to post how i got Ubuntu to work In my PC incase anyone else has the same problem

The problem is caused when you add a nvidia video card to a dell system that has onboard video that can not be disabled in the bios.

the PC will boot up to a command line with a error that the X-Server could not start because it can't detect your display.

Solution:
Remove the added video card
Install Linux
Install driver for removed video card
Turn off pc
Install Removed Card
Power on PC
when it's booted up (it'll be a command line) log in
set a root password (sudo passwd root)
reconfigure Xorg (nvidia-xconfig)
reboot.

if this doesn't work, you can try replacing nvidia-xconfig with either:
sudo dpkg-reconfigure xsever-xorg  
or :
sudo dpkg-reconfigure -phigh xserver-xorg

This is how i got my display to work using a nVidia Geforce FX 5200 (256mb) in a Dell Dimension 3000.

if anyone else out there has this problem, i hope this will help.

subnote: couldn't they modify X-Server to detect which display had a monitor connected to it so the user wouldn't have to figure this out?

::EDIT:: this can probably also work for other types of video cards such as ATI but i don't know what the command is to set them up.
also, i'm a total noob with linux, so i might not be able to answer too many questions about all this stuff, i just wanted to share how i got mine to work incase anyone has the same problem.

---

### Post by Guennarr on 2007-07-10
Hello Scott, 

I own a Dimension 5000 with a Geforce 6800 (256 MB) already included (not a card built in *after* buying it). 

The card works under windows, but despite installation of nvidia drivers I can still run Ubuntu just with a screen resolution of 1024 * 768. (Sidenote windows xp allows considerably higher screen resolution as well as open suse). 

Did anyone experience similar problems?
Thanks in advance for your help! 

Greetings, 
Günther

---

### Post by bigken on 2007-07-10
sudo dpkg-reconfigure xsever-xorg 

or 

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Scotty1982 on 2007-07-11
@ bigken:  thanks, i forgot where i posted this until now, so i didn't notice it had a question posted.

---

### Post by gecko94 on 2007-07-15
I have the the same problem but i have an IBM netvista board and an ati card. will this still work for me?

---

### Post by bigken on 2007-07-15
is there nothing thats says something like 1st boot device agp or pci ?

---

### Post by terrapisces on 2007-07-15
If the video card that you are trying to disable is an onboard card, then just disable it in the bios. Any onboard-mobo worth anything will have the option to disable the onboard peripherals. You will still have to follow any instructions for installing the new card, but this should remove the old device alltogether.

---

### Post by gecko94 on 2007-07-16
these are my options:
pci 
agp
integrated

if I select integrated then all will display except for the loading screen which will only display through my pci card
but if I choose pci, it will say xserver can't start because it can't detect my screens and if I try to configure xserver it will always say my active video is my integrated.
btw i have a radeon 9200 mac edition that i flashed over to a pc 9200 le ( the other versions of the bios wouldn't download) it works fine in xp

---

### Post by terrapisces on 2007-07-16
What model is the board? If possible, is there a bios update for it? I've never found a board that didn't allow you to disable the onboard devices if you want to use another add-on.

---

### Post by bg1256 on 2007-07-16
> **Guennarr said:**
> Hello Scott, 

I own a Dimension 5000 with a Geforce 6800 (256 MB) already included (not a card built in *after* buying it). 

The card works under windows, but despite installation of nvidia drivers I can still run Ubuntu just with a screen resolution of 1024 * 768. (Sidenote windows xp allows considerably higher screen resolution as well as open suse). 

Did anyone experience similar problems?
Thanks in advance for your help! 

Greetings, 
Günther

You may need to manually add other desired resolutions.

sudo gedit /etc/X11/xorg.conf

Locate the "screen" section.

My default depth is 24. Find yours, and then manually add the resolution you want to your default resolution's subsection.

Here's my xorg.conf, and I had to add 1280x1024 manually.

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
   *** DefaultDepth    24***
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
   [B][I]     Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"[/I][/B]
    EndSubSection

---

### Post by gecko94 on 2007-07-17
> What model is the board? I'm not really sure because I can't find any numbers on it. I think it's one of [these]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42922")
> If possible, is there a bios update for it? I couldn't find the bios updates on the IBM/lenovo website, maybe I should look again.

---

### Post by bigken on 2007-07-17
well if your ati card is agp select agp in the bios and run sudo dpkg-reconfigure -phigh xserver-xorg or sudo dpkg-reconfigure xserver-xorg 

anyhow just stick it in and see what happens ;)

---

### Post by gecko94 on 2007-07-17
It's a pci card and I tried the second one- should I edit the address of my card. also, will envy be able to auto configure this for me if I use that?

---

### Post by bigken on 2007-07-18
so you need to select pci in the bios as to using envy I dont know just give it a go

---

### Post by gecko94 on 2007-07-19
tried that but I just screwed up the xorg/xserver. I remember all the settings though so I'm gonna reset all the stuff. is there any way to change the video output while in the OS? also envy recognizes my card and installs fine so I'm really confused.

This might sound odd but do you think that if I added an agp card but set my bios to pci that it may work? I've heard that onboard intel graphics cards won't be disabled all the way with a pci, only agp. Should I try this? btw just to clarify I have a pci not a pci-e card. 
Thank you;).

*EDIT--I forgot to mention that I installed using the alternate cd so I could do it in text mode on my card but I still couldn't use it afterwards.

---

### Post by gecko94 on 2007-07-20
nevermind, I got the card to work. the pci bus setting was wrong.

---

### Post by Scotty1982 on 2007-10-17
> **terrapisces said:**
> If the video card that you are trying to disable is an onboard card, then just disable it in the bios. Any onboard-mobo worth anything will have the option to disable the onboard peripherals. You will still have to follow any instructions for installing the new card, but this should remove the old device alltogether.

a lot of dells don't have a option to completely disable the onboard video. you can make the added card the default, but it still causes problems because the integrated is not disabled.

i agree any decent mobo will have the option to disable it, but dell doesn't use decent mobo's. that's why this is posted in the dell support forum.

i now can get it to boot using 'safe graphics mode' though, so that's working better.

---

