---
title: "Screensaver issues"
date: 2014-01-27
forum: Desktop Environments
---

### Post by jsharp on 2014-01-27
I have a fresh install of Ubuntu (Server) 12.04.3 LTS and I went to [this website]("http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/") to add some more screensavers. So far, I have enjoyed them but I am now having issues with one in particular. The one I'm having trouble with is called **GLMatrix** found [here]("http://www.jwz.org/xscreensaver/screenshots/"). It use to work -- after I ran some updates, it stopped working. I did not see anything in the way of video driver updates but it's possible that could be an issue I presume? Has anyone else experienced issues like this before? If so, what fix did you put in place?

Thanks

[COLOR=#ff0000]****Update***[/COLOR]

[Here]("https://app.box.com/s/ks20xy0zytfk2hpy6i09")  is what is displayed when I select the GLMatrix screensaver. Has anyone  had this happen before? If so, what is the solution? Again, this  screensaver use to work for me - but for some reason, does not anymore  and I do not understand why.

Thanks!

---

### Post by jsharp on 2014-01-28
So...no one else has this issue? Hoping to find out if anyone has a fix on this or not? :confused:

---

### Post by stinkeye on 2014-01-28
Do any of the GL screensavers work?
Check your gfx driver...
```
lspci -nnk | grep -iA2 vga
```

FYI I installed and tested xscreensaver here on an up to date 13.10 and glmatrix works.
```
[COLOR="#008000"]glen@Saucy:~$[/COLOR] **lspci -nnk | grep -iA2 vga**
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:351a]
	Kernel driver in use: [COLOR="#FF0000"]nvidia[/COLOR]
```

---

### Post by jsharp on 2014-01-28
@stinkeye

```
jsharp@Sharp001:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670] [1002:6758]
    Subsystem: XFX Pine Group Inc. Device [1682:3181]
    Kernel modules: radeon
--
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670] [1002:6758]
    Subsystem: XFX Pine Group Inc. Device [1682:3181]
    Kernel modules: radeon
```

This is what I'm currently running. Do you have any other suggestions that I could try? I'm very new to ubuntu, so any information would be helpful!

Thanks!

---

### Post by stinkeye on 2014-01-28
Don't know a lot about amd gfx but you appear to be using the open source driver.

In a terminal see if you can run **glxgears**
glxgears is in the **mesa-utils** package from the [**_[COLOR="#B22222"]“Universe” repository[/COLOR]_**]("http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository").

You say your running Ubuntu (**Server**) 12.04.3 LTS so don't really know what you installed for a graphical environment.
May have to install/reinstall the proprietary fglrx driver.
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by jsharp on 2014-01-29
```
jsharp@Sharp001:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
```

This is the output I get when I do **glxgears**. For my GUI, I used this:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop
```

When I do **lspci -vvnn | grep VGA**, I am not sure what I'm looking for? There are so many entries. I think I know what I'm looking for, but I'm not 100% sure. Some help please?

```
jsharp@Sharp001:~$ lspci -vvnn | grep VGA
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670] [1002:6758] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670] [1002:6758] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
```

Thanks for your continued help, very much appreciated!

---

### Post by stinkeye on 2014-01-29
If you installed ubuntu-desktop you can get gfx info with....
```
/usr/lib/nux/unity_support_test -p 
```
eg my output using the proprietary nvidia drivers...
```
[COLOR="#008000"]glen@Saucy:~$[/COLOR] **/usr/lib/nux/unity_support_test -p **
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 319.32

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

Try installing the amd gfx driver using the command line as described here ...**_[COLOR="#B22222"][2.1. Installing via the command line ]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Installing_via_the_command_line")[/COLOR]_**

---

### Post by jsharp on 2014-01-29
When I run the following code (**sudo apt-get install fglrx fglrx-amdcccle**), the install crashes. I am not able to view the errors as it continues to error out on me.

**[SIZE=4]*Update*[/SIZE]** The fglrx application will crash on me every single time. It doesn't like that driver? 

When I run **sudo apt-get remove --purge fglrx fglrx-amdcccle** and **sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates**

The glmatrix screensaver works. However, when I try to use the fglrx app, it fails. Every time. I want to say thank you again for your help and I think I now understand what the issue is.
:)

---

### Post by stinkeye on 2014-01-29
OK ,
```
/usr/lib/nux/unity_support_test -p 
```
will tell you what driver is in use.
eg
```
[COLOR="#008000"]glen@Saucy:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 [COLOR="#FF0000"]NVIDIA 319.32[/COLOR]
```
Good luck.

---

### Post by jsharp on 2014-01-30
```
jsharp@Sharp001:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD TURKS
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

That is the output I get after running **/usr/lib/nux/unity_support_test -p**

Appreciate your support! :KS

---

