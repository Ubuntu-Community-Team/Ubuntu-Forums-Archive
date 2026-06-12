---
title: "Can't  enable KWin effects with ATI X1270/fglrx"
date: 2009-03-27
forum: Desktop Environments
---

### Post by zak89 on 2009-03-27
I am running Ubuntu Intrepid, but I installed Kubuntu-Desktop/KDE4 as well. I have installed the fglrx driver using the Restricted Drivers utility. It seems to work fine in GNOME; the effects look good. However, in KDE, if I enable the KWin effects, I get the following error:

"Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type."

I checked to see what driver I have loaded for the video card:

```
#lspci -vv
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
        Subsystem: Dell Device 0206                                                 
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 64, Cache Line Size: 64 bytes                                                               
        Interrupt: pin B routed to IRQ 19                                                                    
        Region 0: Memory at e0000000 (64-bit, prefetchable) [size=256M]                                      
        Region 2: Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]                                   
        Region 4: I/O ports at ee00 [size=256]                                                               
        Region 5: Memory at fea00000 (32-bit, non-prefetchable) [size=1M]                                    
        Capabilities: [50] Power Management version 2                                                        
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)                   
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                  
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-                      
                Address: 0000000000000000  Data: 0000                                                        
        Kernel driver in use:** fglrx_pci **                                                                     
        Kernel modules:** fglrx**       
```

So it appears that the correct driver is loaded. Is there some xorg.conf change I should make to enable compositing for KWin?

Thanks!

---

### Post by HavocXphere on 2009-03-27
Not sure how much of this is applicable to your setup, but for my ATI card the settings are:

Composting ON/OFF is controlled by this setting:
/home/ms/.kde/share/config/kwinrc
```
[**Compositing**]
Backend=OpenGL
Enabled=**true**
GLDirect=true
GLMode=TFP
GLTextureFilter=1
GLVSync=false
HiddenPreviews=0
XRenderSmoothScale=false

```

And *my* xorg.conf
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option "TexturedVideo" "off"        
        Option "UseFastTLS" "2"
        Option "RenderAccel" "true"
EndSection

```

Does the restricted module thing show the driver as activated?

---

### Post by zak89 on 2009-03-27
Hmm, that doesn't seem to change anything. 

Yes, the Restricted Drivers tool shows the ATI driver as activated.

---

### Post by zak89 on 2009-03-27
Sorry for the bump, but does anyone have any ideas about this?

---

### Post by dE_logics on 2009-04-02
May be new drivers?

Check this out - 

[http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html](http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html)

Try and let me know.

---

### Post by CHaoSlayeR on 2009-12-06
Although this is an old thread I want to make things clear:

fglrx has abandoned support for ALL chips before the HDxxxx series since driver release 9.4 because the backwards compatibility layer in the driver (up to 9.3) made things even worse.

For all chips of Radeon X1xxx cards and older ones the open-source radeon driver (package xserver-xorg-video-radeon) is supposed to be stable and features full OpenGL acceleration (although some games might run into trouble because some GL-Extensions are missing, namely Quake4/Doom3/...).

C]-[aoZ

---

