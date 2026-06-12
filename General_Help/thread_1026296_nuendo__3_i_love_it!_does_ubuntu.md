---
title: "nuendo  3 i love it! does ubuntu?"
date: 2008-12-31
forum: General Help
---

### Post by vtek on 2008-12-31
hows it goim folks. i recently installed ubuntu 64 onto my pc mainly so i could utilize the 8gb of ram xp pro sp3 32bit could not. im an avid music producer and with using such processor/memory heavy programs and synths you can understand why i need this headroom. 
im using nuendo 3 with xp but i was wondering how the hell do i install it onto the ubuntu os. i thought that if i set up ubuntu onto a seperate partition i could use the installed program or at least re-install it again onto ubuntu but unfortunately not a thing happened apart from a message saying could not locate the executable file. forgive my ignorance but i am completely new to this os. i love what has been done to it from the gui side which makes the transition from windows alot easier and less daunting but nevertheless i think i will need alot of help adjusting to my new environment.
i also have a dual monitor setup but i cant figure out how run them as one large monitor rather than two screens doing the same thing at the same time (POINTLESS!)
any help on this issue would be great and ill even write a song for anyone who successfully helps resolve this situation.
thanks! at your mercy till i understand!
VTEK

---

### Post by ubuntu27 on 2008-12-31
Wine is a program that lets you run Windows application in Linux. Please note that not all applications work with this.

It seems that Nuendo 3.2 can be run in GNU/Linux with [Wine]("http://www.winehq.org/").


Wine's [Applications Database]("http://appdb.winehq.org/"): [Nuendo]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6623")



Here is the guides on how to Install Wine
[How to install Wine in Ubuntu]("http://www.psychocats.net/ubuntu/wine")

---

### Post by vtek on 2009-01-01
thanks a million for that appreciate the help. i was just wondering would it matter that i installed nuendo onto xp32 and would there be any form of conflict seeing as though ill be running nuendo 3 on ubuntus 64bit os?
thanks again for the help and a very happy new year to you!

---

### Post by bartvh on 2009-01-01
It doesn't matter. As far as Ubuntu is concerned, your XP installation doesn't exist.

---

### Post by vtek on 2009-01-01
thanks, can you tell me how i can install drivers etc. i have an Nvidia 8600 gt gpu and i downloaded the appropriate linux driver for it but when i double clicked it it wouldnt open. i right clicked it then and went to open with autorun prompt but the same problem occured. then i tried to open with a custom command which i found on the site i downloaded the driver from "sh NVIDIA-Linux-x86_64-177.82-pkg2.run" but still no driver installation, is there a problem in the command line or am i going about this completely wrong. thanks for any help you can give.

---

### Post by onero on 2009-01-01
Regarding the NVIDIA driver installation, you have to install it while X (basically the GUI) isn't running. Upon bootup into Ubuntu, you'll see an option for booting up into Ubuntu Recovery Mode or something like that;  choose that and you'll boot up into the terminal without the GUI running. You can run the command there and it should work. 

There are some questions and things in the installation, but for me I just basicallty answered yes to everything and experienced no problems. Good luck!

---

### Post by vtek on 2009-01-01
thanks very much for your help. ill give that  try and ill let you now how i get on thanks again

---

### Post by jerome1232 on 2009-01-01
Just butting in becuase that's the **difficult** way to install nvidia drivers, have you tried the restricted driver manager and/or envy first?

I would recomend ensuring your system is completly up-to-date before install the driver: System->Adminitrastion->Update Manager, click check, then update if there are any.

Restricted Driver Manager:

System->Administration->Hardware Drivers, It should suggest a driver in here, you just select it and click  activate. A restart will be needed for the change to take affect.

Envyng: This is a program that will download the latest drivers and install them.

```
sudo apt-get update
sudo apt-get install envyng-gtk
sudo envyng -t
```

As a last resort we can walk you through using Nvidia's installer but it's not nearly as easy as these other methods.

---

### Post by dagnabit dang doohickey on 2009-01-01
If, by any chance, you find that wine is a cold black hole of hopelessness and despair, have a look at [ardour]("http://ardour.org/"). :)

---

### Post by vtek on 2009-01-01
i tried using wine to install nuendo but i got an error message. the installer opened but after the first couple of clicks the error message appeared when trying to install the dongle (usb key) emulator. can anyone give me a little advice on this thanks.

---

### Post by vtek on 2009-01-01
i tried using wine to install nuendo but i got an error message. the installer opened but after the first couple of clicks the error message appeared when trying to install the dongle (usb key) emulator. can anyone give me a little advice on this thanks.

---

### Post by vtek on 2009-01-01
had a little trouble installing nuendo with wine. the installation process opened up fine but when i was instaling the dongle (usb key) emulator it gave me an error message. this was basically the first option of the installation. is there something i am overlooking? considering that im popping my linux cherry im sure theres a hell of alot of things i am overlooking but nuendo is the only thing i really want to install at the moment so any help at all would be great

---

### Post by vtek on 2009-01-01
im not ready to move to a new daw just yet as im really comfortable with nuendo at the moment but for future reference does ardour support vsts?

---

### Post by dagnabit dang doohickey on 2009-01-01
> **vtek said:**
> im not ready to move to a new daw just yet as im really comfortable with nuendo at the moment but for future reference does ardour support vsts?

Yes, but due to licensing restrictions, ardour needs to be [compiled to enable vst]("http://ubuntuforums.org/showthread.php?t=801718").

---

