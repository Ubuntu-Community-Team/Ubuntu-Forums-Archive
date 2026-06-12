---
title: "mupen64 trouble"
date: 2008-08-01
forum: Gaming &amp; Leisure
---

### Post by dbbolton on 2008-08-01
I downloaded mupen64 and the test demos from the website, but I can't get any picture when I try to play games. glxgears cranks out around 3400 fps, so I'm pretty sure my GPU can handle mupen. Here is some sample output:

```

Couldn't load plugin '/home/daniel/Source/mupen64-0.5/plugins/glN64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/daniel/Source/mupen64-0.5/plugins/mupen64_soft_gfx.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/daniel/Source/mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/daniel/Source/mupen64-0.5/plugins/ricevideo.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/home/daniel/Source/mupen64-0.5/plugins/Glide64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
rom size: 1310720 bytes (or 1 Mb or 8 Megabits)
file found
rom size: 1310720 bytes (or 1 Mb or 8 Megabits)
byteswaping rom...
rom byteswaped
rom loaded succesfully
80 37 12 40
ClockRate=f
Version:1444
CRC: 81361532 2aeb643f
name:                     
Manufacturer: 0
Cartridge_ID: 0
Country Code : 0
size: 4096
PC= 80140000
md5 code:674D416C2BD1EF0192BEE34AA260B21A
eeprom type:0
init timer!
rom size: 2097152 bytes (or 2 Mb or 16 Megabits)
file found
rom size: 2097152 bytes (or 2 Mb or 16 Megabits)
byteswaping rom...
rom byteswaped
rom loaded succesfully
80 37 12 40
ClockRate=f
Version:1444
CRC: 8f5179c4 803526dc
name: Space Rotator       
Manufacturer: 0
Cartridge_ID: 0
Country Code : 0
size: 4096
PC= 80200000
md5 code:1934618C99A70DD8E74305C6DB06CAF3
eeprom type:0
init timer!
memory initialized
[blight's SDL input plugin]: version 0.0.10 initialized.
TR64GL : (II) Getting video info..TR64GL : (II) Setting video mode 640x480x32..demarrage r4300
dynamic recompiler
PC=80200738:24c60002
reg[ 0]:       0       0        reg[16]:ffffffff92492493
reg[ 1]:ffffffff80230000        reg[17]:       036406c81
reg[ 2]:       0       1        reg[18]:       0       0
reg[ 3]:ffffffff80118636        reg[19]:       0       0
reg[ 4]:       0    28d4        reg[20]:       0       0
reg[ 5]:       0      18        reg[21]:       0       0
reg[ 6]:ffffffff80248ff8        reg[22]:       0       0
reg[ 7]:       0    c300        reg[23]:       0       0
reg[ 8]:ffffffff80248fc8        reg[24]:       0218554e3
reg[ 9]:       0      9c        reg[25]:       0       0
reg[10]:       0   3b633        reg[26]:ffffffffa430000c
reg[11]:       06eff2c76        reg[27]:       0     aaa
reg[12]:ffffffff802561c8        reg[28]:       0       0
reg[13]:       0      f0        reg[29]:ffffffff8022d200
reg[14]:       0218554e0        reg[30]:       0       0
reg[15]:       0218554e2        reg[31]:ffffffff802002b0
hi:       0 99005be        lo:       01e9bb399
apr&#65533;s 361102004 instructions soit 1585fab4
[blight's SDL input plugin]: Closing...

Any help would be appreciated.

```

---

### Post by csi_ on 2008-08-01
Check out mupen64plus, it's more up to date: 
[http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

---

### Post by dbbolton on 2008-08-02
> **csi_ said:**
> Check out mupen64plus, it's more up to date: 
[http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)
Thanks, this seems to be working :)

Just one problem. It seems that with the 32 bit binary, only the basic input plugin is available in the preferences dialog, but the blight input plugin is in the plugin folder. Any idea why?

EDIT:

I had to install 'libsdl-ttf2.0-0'. Apparently future version of the blight plugin won't have this dependency.

---

### Post by truchisoft on 2008-08-18
Thank you for posting the solution, care to share where did you found the missing dependency? I have been looking like crazy for a solution until i found yours.

Thanks again!!

---

### Post by dbbolton on 2008-08-18
> **truchisoft said:**
> Thank you for posting the solution, care to share where did you found the missing dependency? I have been looking like crazy for a solution until i found yours.

Thanks again!!
I installed it through synaptic. I know it's in the Debian unstable repositories, but I'm not sure about Ubuntu.

---

