---
title: "heroes of newerth"
date: 2009-12-20
forum: Gaming &amp; Leisure
---

### Post by zaffe93 on 2009-12-20
hi. 

i downloaded heroes of newerth but when i launch it, it shuts itself down !?!? why lol

---

### Post by Vadi on 2009-12-20
go to system - administration - hardware drivers and install the recommended video driver

---

### Post by zaffe93 on 2009-12-21
already done that..

plz help!

---

### Post by Ferrat on 2009-12-21
start HoN in a terminal and paste the output

---

### Post by zaffe93 on 2009-12-21
> **Ferrat said:**
> start HoN in a terminal and paste the output

hur startar jag den genom terminal?:P

---

### Post by zaffe93 on 2009-12-21
anonymous@4comp:~$ cd HoN
anonymous@4comp:~/HoN$ /hon.sh
bash: /hon.sh: No such file or directory
anonymous@4comp:~/HoN$ ./hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: ARB_shader_objects not available.
anonymous@4comp:~/HoN$ 




WHYYYYYYYYYYYYYYYYYYYY

---

### Post by Grenage on 2009-12-21
I'd double-check the MD5 of the install file.

---

### Post by zaffe93 on 2009-12-21
> **Grenage said:**
> I'd double-check the MD5 of the install file.

the md5 ? install file ? where can i find it :confused:
i just got ubuntu yesterday so i'm a bit newbie

---

### Post by zaffe93 on 2009-12-21
Help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me help help help me

---

### Post by Milos_SD on 2009-12-21
K2 - Fatal Error: ARB_shader_objects not available.

As it says, your graphic card driver doesn't have ARB_shader_objects extension. Do you have ATI 9xxx series card?

---

### Post by zaffe93 on 2009-12-21
> **Milos_SD said:**
> K2 - Fatal Error: ARB_shader_objects not available.

As it says, your graphic card driver doesn't have ARB_shader_objects extension. Do you have ATI 9xxx series card?

so how could i play this game before i got ubuntu...?

i dont know what ati 9xxx series card is.

i bought this computer somewhere in 2006 lol

---

### Post by egravede on 2009-12-21
> **zaffe93 said:**
> so how could i play this game before i got ubuntu...?

i dont know what ati 9xxx series card is.

i bought this computer somewhere in 2006 lol

sounds like your graphics card is old
they recently patched HoN and upped some of the visuals and recently released games require Shader 3.0

---

### Post by zaffe93 on 2009-12-21
> **egravede said:**
> sounds like your graphics card is old
they recently patched HoN and upped some of the visuals and recently released games require Shader 3.0

lol, listen, i could play this game before i got ubuntu. it was yeterday!!!!!!!!!!!

---

### Post by Zayfox on 2009-12-23
Ugh.
A whole post filled with 'help' and also repeated and wayy too much use of "!".
If it was working "Before you got Ubuntu", which seemed to be not long ago, are you actually using the Linux version of HoN?

---

### Post by moonshine2b1 on 2009-12-23
I think your PC doesn't meet the minimum requirements for it read it clearly and try again also (VGA card) 

[]("http://www.cheapmindflex.com")

---

### Post by nick_geetar on 2010-01-07
Hey just downloaded the game but when I go to run it in terminal this comes up:
nick@nick-laptop:~$ '/home/nick/Desktop/HoNClient-0.2.1.41.sh' 
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.349153 s, 447 kB/s
Segmentation fault

---

### Post by Rodney9 on 2010-01-07
Where can I down load it from ?

---

### Post by Pasdar on 2010-01-07
> **nick_geetar said:**
> Hey just downloaded the game but when I go to run it in terminal this comes up:
nick@nick-laptop:~$ '/home/nick/Desktop/HoNClient-0.2.1.41.sh' 
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.349153 s, 447 kB/s
Segmentation fault

do
chmod +x game.sh

so in your case: **chmod +x /home/nick/Desktop/HoNClient-0.2.1.41.sh**

then do
**./home/nick/Desktop/HoNClient-0.2.1.41.sh**

with the .

If that doesn't work, maybe the file is incompletely downloaded. What videocard do you have?

---

### Post by nick_geetar on 2010-01-07
I have the Nvidia 1750 with the 190.53 driver.when I did as you replied I got this:
nick@nick-laptop:~$ ./home/nick/Desktop/HoNClient-0.2.1.41.sh
bash: ./home/nick/Desktop/HoNClient-0.2.1.41.sh: No such file or directory
 I just checked to make sure I had made a complete download and it was.
Any other ideas?

---

### Post by Pasdar on 2010-01-07
> **nick_geetar said:**
> I have the Nvidia 1750 with the 190.53 driver.when I did as you replied I got this:
nick@nick-laptop:~$ ./home/nick/Desktop/HoNClient-0.2.1.41.sh
bash: ./home/nick/Desktop/HoNClient-0.2.1.41.sh: No such file or directory
 I just checked to make sure I had made a complete download and it was.
Any other ideas?

Did you remove it from your desktop? Read what it says... no such file... where is the downloaded file located? Also I've never heard of that model nvidia... is it really 1750? if yes, then that 1 refers to the generation... which means its very very old... however, if it works with the drivers you mentioned, it must be that old and i dont think its 1750.

---

### Post by nick_geetar on 2010-01-07
Sorry bout that it was suppose to say 7150. It's a 7 series notebook model. No I did not remove the link from my desktop.

---

### Post by alex3047 on 2010-01-07
heroes of newer this very good game i like it....... but it is very difficult to install.

---

### Post by Pasdar on 2010-01-07
Just right click on the file, go to properties, permissions, and add execution rights to the file.. then run the file.

---

### Post by nick_geetar on 2010-01-07
Already did that man.

---

### Post by Pasdar on 2010-01-07
I dont think you've actually ran it. The second error you showed me implies that you didn't even run the file. (trying to run something that doesn't exist at that address).

try

**sh HoNClient-0.2.1.41.sh**

---

### Post by nick_geetar on 2010-01-07
Says it can't open it. I did ./HoNCLient-0.2.1.41.sh and got this:
nick@nick-laptop:~$ cd /home/nick/Desktop
nick@nick-laptop:~/Desktop$ ./HoNClient-0.2.1.41.sh
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.139548 s, 1.1 MB/s
Segmentation fault
nick@nick-laptop:~/Desktop$

---

### Post by maddogtet on 2010-01-07
i got the same problem
grafic device: ati mobility x1800

 ```
~/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: ARB_shader_objects not available
```Can anyone help?

```
glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Projec
``````
glxinfo | grep "direct rendering"
direct rendering: Yes
```

My Xorg.conf looks so: 
```

Section "Device"
        Identifier      "Radeon x1800"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AccelMethod" "XAA"
        Option          "TripleBuffer" "True"
        Option          "DynamicClocks"  "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon x1800"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

---

### Post by kforum on 2010-01-07
ATIs on linux=trouble, but i'd advise anyone with gfx card issues to go over to the main forum's support section and ask there(the HoN forums).


cheers

---

### Post by Pasdar on 2010-01-08
> **maddogtet said:**
> i got the same problem
grafic device: ati mobility x1800

 ```
~/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: ARB_shader_objects not available
```Can anyone help?

```
glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Projec
``````
glxinfo | grep "direct rendering"
direct rendering: Yes
```

My Xorg.conf looks so: 
```

Section "Device"
        Identifier      "Radeon x1800"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AccelMethod" "XAA"
        Option          "TripleBuffer" "True"
        Option          "DynamicClocks"  "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon x1800"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

It mentions that you dont have "ARB_shader_objects" support. So it definately has to with your videocard or the drivers. I know your videocard is weak, but i'm not sure whether it has that or not... what drivers are you using? Im using 9.12 ...

---

### Post by Pasdar on 2010-01-08
maddogtet, I just checked and I think 'ARB_shader_objects' is not supported for your card in Linux. The latest drivers you could use would be 9.3 ... and ARB_shader_objects only came in version 9.8 as far as I know... but you cant use those drivers since they dont support your card... however on windows the driver support goes until 9.11 ...

try the open source drivers... check topic in cafe... those support much more for your card.

---

### Post by nick_geetar on 2010-01-08
Does anyone got an Idea about my error?

---

