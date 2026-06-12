---
title: "How do I enable direct rendering?"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by miLl3niUm on 2007-07-01
I want it for several reasons.

Thank You :)

---

### Post by Ceriel Nosforit on 2007-07-01
You might want to back up your xorg.conf file if this doesn't work. To do so, open the console and and issue:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If you have a nVidia card, already installed and working, you add " Option "RenderAccel" "True" " under the "Device" section of your xorg.conf file in the directory /etc/X11 like so:

```
Section "Device"
      Identifier     "nVidia Corporation NV43 [GeForce 6600]"
      Driver         "nvidia"
      Option         "RenderAccel" "True"
  EndSection

```
Then you start your X server again by either rebooting or or hitting Ctrl-Alt-Backspace.

If the X server fails to start, hit Ctrl-Alt-F1, log in and issue the command
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And then reboot.

You might want to print or write down these instructions on paper.

---

### Post by miLl3niUm on 2007-07-01
What about ATI Radeon 9200?

---

### Post by rivera151 on 2007-07-01
> **miLl3niUm said:**
> What about ATI Radeon 9200?

Just follow [this]("href=https://help.ubuntu.com/community/BinaryDriverHowto/ATI") link and you should be set.  Make sure you backup your xorg.conf like above before you take the first step.  Good luck!

---

### Post by steveneddy on 2007-07-01
> **rivera151 said:**
> Just follow [this]("href=https://help.ubuntu.com/community/BinaryDriverHowto/ATI") link and you should be set.  Make sure you backup your xorg.conf like above before you take the first step.  Good luck!

DEAD LINK.....

---

### Post by kpolice on 2007-07-01
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by deanlinkous on 2007-07-01
AFAIK the radeon driver has a binary blob - if that bothers you....if not, then no worries...

---

### Post by miLl3niUm on 2007-07-02
> **steveneddy said:**
> DEAD LINK.....

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by RandomXcore on 2007-07-04
> **Ceriel Nosforit said:**
> You might want to back up your xorg.conf file if this doesn't work. To do so, open the console and and issue:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If you have a nVidia card, already installed and working, you add " Option "RenderAccel" "True" " under the "Device" section of your xorg.conf file in the directory /etc/X11 like so:

```
Section "Device"
      Identifier     "nVidia Corporation NV43 [GeForce 6600]"
      Driver         "nvidia"
      Option         "RenderAccel" "True"
  EndSection

```
Then you start your X server again by either rebooting or or hitting Ctrl-Alt-Backspace.

If the X server fails to start, hit Ctrl-Alt-F1, log in and issue the command
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And then reboot.

You might want to print or write down these instructions on paper.
what if it still doesnt enable direct rendering?
i changed the ifconfig file and saved and rebooted but it comes up with serenity@serenity-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No

---

### Post by FuturePilot on 2007-07-04
> **RandomXcore said:**
> what if it still doesnt enable direct rendering?
i changed the ifconfig file and saved and rebooted but it comes up with serenity@serenity-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No

RenderAccel is not direct rendering. To get direct rendering go to the very bottom of your xorg.conf and make sure this section is present. If it's not add it
```
Section "DRI"
        Mode    0666
EndSection

```
Then go up to the Module section and add```
Load          "dri"
```

---

### Post by RandomXcore on 2007-07-04
thanks, the xorg.conf has those in the section already. it must be something to do with the drivers i have to update for my video card. i found the driver and i cant install it . how do i install a rpm file?

---

### Post by FuturePilot on 2007-07-04
Are you using Feisty? Just open the Restricted Driver Manager System>Administration and enable the driver.
You can't install RPMs on Ubuntu since Ubuntu is based on Debian.

---

### Post by RandomXcore on 2007-07-04
im using gNewSense.

---

### Post by RandomXcore on 2007-07-08
so how would i be able to enable direct rendering on gNewsense?

---

### Post by isaacj87 on 2007-07-08
what type of video do you have? ati, nvidia, intel....?

---

### Post by RandomXcore on 2007-07-08
my video card is Intel 82810E DC-133 CGC

---

### Post by RandomXcore on 2007-07-13
> **RandomXcore said:**
> my video card is Intel 82810E DC-133 CGC

so then i went and downloaded the update for my video card on the intel website.
once i had done that, the instructions on the graphics release note said :

             Install the XFCom_i810 server
You will need to be the root user to do this.
    cd /path_to_downloaded_rpm
    rpm -Uvh XFCom_I810-1.2-3.i386.rpm

and i did, but it comes up with this message:

root@serenity-desktop:/home/serenity/software# rpm -Uvh XFCom_|810-1.2-3.i386.rpm
bash: 810-1.2-3.i386.rpm: command not found
error: open of XFCom_ failed: No such file or directory

so basically i cant install the rpm file on my own and i need someone to help me sort it out.

---

### Post by rinch on 2007-07-13
It might be just a typo? - I see a pipe "|" in the text you quoted where there should be a letter "I"

that would also explain the message from bash which is telling you that it doesn't recognise the filenames of the text before and after the "|"

try copying this text and pasting it into a terminal:
```
rpm -Uvh XFCom_I810-1.2-3.i386.rpm
```

---

### Post by RandomXcore on 2007-07-13
no what you saw was not a typo. i put a pipe in the command line, and youre prolly right it wasnt supposed to be a pipe.
but i tried your command line in terminal as well and it came up with the same thing ...

root@serenity-desktop:/home/serenity/software# rpm -Uvh XFCom_I810-1.2-3.i386.rpm
error: open of XFCom_I810-1.2-3.i386.rpm failed: No such file or directory

then i tried this 

rpm -Uvh XFCom_i810-1.2-3.i386 

and it needed dependencies.
        ld-linux.so.2 is needed by XFCom_i810-1.2-3.i386
        libc.so.6 is needed by XFCom_i810-1.2-3.i386
        libdl.so.2 is needed by XFCom_i810-1.2-3.i386
        libm.so.6 is needed by XFCom_i810-1.2-3.i386
        /bin/sh is needed by XFCom_i810-1.2-3.i386
        libc.so.6(GLIBC_2.0) is needed by XFCom_i810-1.2-3.i386
        libc.so.6(GLIBC_2.1) is needed by XFCom_i810-1.2-3.i386
        libdl.so.2(GLIBC_2.0) is needed by XFCom_i810-1.2-3.i386
        libdl.so.2(GLIBC_2.1) is needed by XFCom_i810-1.2-3.i386
        libm.so.6(GLIBC_2.0) is needed by XFCom_i810-1.2-3.i386
 
so ill get them then get back to ya :-)

---

### Post by RandomXcore on 2007-07-15
um i have tried to download the rpm file that has all those dependencies in it but i cant install it. it is called pxes-base-0.5-RC3.i386.rpm coz it needs some dependencies too they are
tftp-hpa-server >=0.28
dhcp >=2.0pl5
/bin/sh
and i dont know how to get them..
this is the hardest thing ever. help me!

---

### Post by RandomXcore on 2007-07-20
man this **** is wack...after at least 3 months of trying to get my comp anywhere near ready for running stepmania i seem to have gotten nowhere without there being more complications, so im totally giving up, thanks for all your help tho everyone ..
i HATE computers!!:mad:

---

