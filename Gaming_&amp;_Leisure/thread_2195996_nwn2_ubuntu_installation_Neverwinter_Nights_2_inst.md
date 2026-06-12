---
title: "nwn2 ubuntu installation Neverwinter Nights 2 installation guide"
date: 2013-12-27
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2013-12-27
Ok so nwn2 is easier to install than nwn1, I have reciently purchased this game from GOG but I have also owned this game on DVD. For the GOG version make sure you purchase the game from GOG.com first and have your account information ready. Also check out the trouble shooting below. Remember that if you add content that changes the core game, your saves may not work or you may experience crashing at certain points.

**1. Install playonlinux**

I used the one found in the repos


**2. Use the playonlinux install script**

Open playonlinux and click install. Check the box labeled "Testing" and a warning should pop up. Search Neverwinter in the search box. Select "GOG.com-Neverwinter Nights 2:Complete" for the DVD version use the script "NeverWinter Nights 2". For the GOG version you will get a warning, just just select "download the program" follow the prompts and fill in your information when required. The sript will automatically download the game for your, or if you already downloaded it then you may choose the option "Use a setup file in my computer" but I didnt use this method so not sure how that works.


**3. You will need Directx9, Devenum, Dxdiag, and vcrun 2005, possibly a few other others just for funzies**

Open playonlinux (may still be open) and highlight "NeverwinterNights2_gog", then select the configure
button. Go to the "install components" tab, you need to install "vcrun 2005", "d3dx9", "Dxdiag" and "Devenum". As extras I like to install these others to but they are optional: "Dxfullsetup", "d3dx10"," d3dx11", "vcrun2008", "gdiplus", "video driver", and "Microsoft Core fonts" (check trouble shooting section when using "Video Driver" if you also have an onboard graphics card.).


**4. You need to configure your installation**

You will need to configure wine so that "Dxdiag" and "Devenum" are set to native. Again with playonlinux open, highlight "NeverwinterNights2_gog" and right click it and select configure wine. In the "libraries" tab set devenum.dll and dxdiag.dll to native. Then also from the playonlinux window select the configure button again. Navigate to the display tab and set:

"GLSL Support" to "enabled"
"Direct Draw Renderer" to "opengl"
"Offscreen Rendering Mode" to "fbo"
"Video Memory Size" to "whatever your video card has, or a little lower"


**5. Enjoy!**

The game should be working at this point. You can add the rest if you want, they improve the game and performance. Here are some useful registry settings to put in the wine registry editor (open playonlinux and right click neverwinter nights 2, select Registry editor, make sure you are in the direct3d file under HKEY_CURRENT_USER-Software-Wine-Direct3d)

DirectDrawRenderer	"opengl"	
Multisampling		"default"	
OffscreenRenderingMode  "fbo"	
PixelShaderMode         "enabled"	
RenderTargetLockMode    "auto"	
StrictDrawOrdering	"default"	
UseGLSL                 "enabled"	
VertexShaderMode	"Hardware"	
[COLOR="#40E0D0"]VideoMemorySize         "128" 	
VideoPciDeviceID	"2a02"		
VideoPciVendorID	"8086"		[/COLOR]

The teal ones will have to have the values of your graphics card. more on this in the troubleshooting section under "Video Driver"



**[COLOR="#FF0000"]Extras![/COLOR]**

**AMD 64 users**

There is an included executable designed to be optimal for 64bit computers, it is called nwn2main_amdxp. Open playonlinux, select  "NeverwinterNights2_gog" and click configure. Select "make a new shortcut from this virtual drive". Select "nwn2main_amdxp.exe" and then you can start the game using this launcher. I havent tried this in a 64 bit version of wine but I use it to startup nwn2 in the 32 bit prefix created.

**Add an Opengl wrapper!**

I like to add this little gem [COLOR="#FF0000"][Direx10 patch for windows xp]("http://www.softpedia.com/get/System/OS-Enhancements/DirectX-10-for-Windows-XP.shtml")[/COLOR], download and unzip it. To install this open playonlinux, highlight "NeverwinterNights2_gog" and click the configure button. Navigate to the "miscellaneous" tab and select "run a .exe file in this vitrual drive". Then navigate to your download folder and select the .exe from the folder you unziped to. This file is a wrapper for directx10 and possibly some directx9 calls to use opengl instead, thus simulating directx10. It was made for windows xp users because xp never updated to directx10. This may eliminate some issues with wine and directx.


**I like to add this pack to the game:**

[COLOR="#FF0000"][Click Here]("http://nwvault.ign.com/View.php?view=NWN2HakpaksCombined.Detail&id=58")[/COLOR]

This contains a ton of good stuff for the game all in one convienent package. It has spell fixes, better compaion AI, Light effects, some bug fixes, etc. However if you have previously saved games they will no longer play correctly. You will need to start over but its worth it. I havent tried statring from a save at the end of an act though, you may be able to start from that point but I doubt it. Follow the provided instructions to install, and remember that the overide folder is in your home directory in ubuntu under "Neverwinter Nights 2". Also comanions will stand around without attacking if you dont disable automatic weapon switching, your casters will still cast but if the try to use melee then they will stand around. You change that option by taking possesion of the character, open their character sheet by pressing "c" and then clicking on the behaviors tab.


**Here is a list of many goodies**

[http://social,bioware,com/forum/1/topic/172/index/3173142/1](http://social,bioware,com/forum/1/topic/172/index/3173142/1) (right click and select copy link location and paste in browser address bar, replace the comma's with periods, forums dont like links to this site)

This list is great, I installed all the graphics tilesets, armors and cloaks, basically anything that updated the graphics and many of these are in high resolution. Also some of the things listed by posters is included in the pack above, makes sure if you used that pack that you dont download and install the same files from this list. Essentially I only installed the tilesets and charater touch ups etc.


**[COLOR="#FF0000"]Troubleshooting[/COLOR]**

**ATI graphics cards:**

ATI has issues with shadows and things in this game (physx from nvidia I assume was used) when you start the game, go to options, then select the advanced graphics tab and set all shadows to low.

Also editing the xorg.conf can help with random crashing and performance with ATI cards. make sure your xorg.conf file has these in it under the modules section (always make a back up before editing):

Section "Module"
	Load  "fglrx"
	Load  "dri"
	Load  "glx"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
	Load  "extmod"
	Load  "FGL.renamed.libglx"
EndSection


**Skybox issues:**

Diable or lower anti-aliasing in the game options


**Crashing at the same point during play:**

You will have to redo any save you have after adding some updates or changing core content, you will need to delete your saves and start over.


**"Video Driver" from playonlinux**

If you have an onboard card and a dedicated graphics card then sometimes this option sets incorrect parameters in the wine registry. To check the correct one open terminal and type "lspci" and lspci -n". You will have to find your graphics card in that list in the terminal Here is what my output looks like:

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS4xx PCI Express Port [ext gfx]
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 4
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**[COLOR="#FF0000"]01:05.0[/COLOR]** VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482/RS485 [Radeon Xpress 1100/1150]
01:05.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 1150] (Secondary)
**[COLOR="#000080"]02:00.0[/COLOR]** VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
07:09.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
08:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 01)
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 


shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ lspci -n
00:00.0 0600: 1002:5950 (rev 10)
00:01.0 0604: 1002:5a3f
00:02.0 0604: 1002:5a34
00:07.0 0604: 1002:5a39
00:12.0 0106: 1002:4380
00:13.0 0c03: 1002:4387
00:13.1 0c03: 1002:4388
00:13.2 0c03: 1002:4389
00:13.3 0c03: 1002:438a
00:13.4 0c03: 1002:438b
00:13.5 0c03: 1002:4386
00:14.0 0c05: 1002:4385 (rev 13)
00:14.1 0101: 1002:438c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:438d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
**[COLOR="#FF0000"]01:05.0[/COLOR]** 0300: 1002:5974
01:05.1 0380: 1002:5874
**[COLOR="#000080"]02:00.0[/COLOR]** 0300: _**[COLOR="#DAA520"]1002[/COLOR]:[COLOR="#8B4513"]683f[/COLOR]**_
02:00.1 0403: 1002:aab0
07:09.0 0604: 10b5:8112 (rev aa)
08:00.0 0c03: 1b73:1000 (rev 01)
3f:00.0 0200: 14e4:167b (rev 02)
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

And from here you will need to match up your cards to figure out what you need. The Red one on my computer is the incorrect one that wine tries to use and set parameters for. The blue one is correct, the Yellow number is The VideoPCIVendorID, the brown one is the VideoPCIDeviceID. then you open playonlinux and right click neverwinter nights 2, select Registry editor, make sure you are in the direct3d file under HKEY_CURRENT_USER-Software-Wine-Direct3d and enter these registry keys with your numbers:

VideoPciVendorID	"1002"
VideoPciDeviceID	"683f"
VideoDriver "ati2dvag.dll" (For ati cards only)

---

