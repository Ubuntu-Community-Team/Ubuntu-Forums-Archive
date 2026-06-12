---
title: "Gaming on DELL XPS 17 (controlling the fans, NVIDIA Optimus)"
date: 2013-06-22
forum: Gaming &amp; Leisure
---

### Post by honzi97 on 2013-06-22
Hi everybody,
I'm completely new to Ubuntu. I would like to play games on my DELL XPS 17 L702X. I've got a bunch of questions:
1.) Do graphic-intensive games, like FIFA run on Ubuntu?
2.) How do I know which name is linked with which program in Bumblebee?
3.) How do I control the fans?
4.) Is it possible to get a cooling pad working?
Thanks

---

### Post by DeathByDenim on 2013-06-22
If you install the proprietary drivers from Nvidia and Bumblebee, then yes, you can play graphic-intensive games. As far as I know, FIFA is Windows-only software, so you might run into trouble there. That said, you can try running it through Wine, which has the capability of running Windows software. You can check [www.winehq.org](www.winehq.org) for compatibility.

With bumblebee, you have to explicitly say when the Nvidia card should be used. You do that using optirun (or primusrun) like:
```
optirun mygame
```

I don't know about the fans and cooling pads though. But isn't a cooling pad just powered by USB anyway? That is, no drivers are required? I have no experience with those I must admit.

---

### Post by honzi97 on 2013-06-23
Thanks, but how do I know the program name after optirun. Do I have to write 'fifa.exe'?

---

### Post by oldrocker99 on 2013-06-23
CD to the directory wher you have FIFA, then enter

>optirun wine fifa.exe

...then post your results.

---

### Post by honzi97 on 2013-06-24
Ok, I tried it. That's what I see:
fixme:file:K32EnumPageFilesA (0x2b1fea0, 0x356028) stub
fixme:file:K32EnumPageFilesA (0x2b1fea0, 0x3559b8) stub
fixme:wbemprox:wbem_locator_ConnectServer 0x1425d8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:wbemprox:wbem_locator_ConnectServer 0x1425f0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:wbemprox:wbem_locator_ConnectServer 0x142608, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:wbemprox:wbem_locator_ConnectServer 0x142620, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:wbemprox:wbem_locator_ConnectServer 0x142638, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:wbemprox:wbem_locator_ConnectServer 0x142650, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x3ea3ba4)
fixme:win:EnumDisplayDevicesW ((null),0,0x35de08,0x00000000), stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x3930c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x392c3c,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x2b1fea0, 0x37e9a0) stub
fixme:file:K32EnumPageFilesA (0x2b1fea0, 0x3492bc) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:win:EnumDisplayDevicesW ((null),0,0x3aef94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aeb08,0x00000000), stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:EventRegister {7733e444-c31d-4c81-95e3-d46e17a6a36f}, 0x600f00, 0x3d3ca20, 0x3d3ca18
fixme:advapi:EventRegister {d6f6af8e-328a-45c8-b504-ac2e43a17446}, 0x600f00, 0x3d3ca58, 0x3d3ca50
fixme:advapi:EventRegister {4f841543-0aa3-4313-a232-85ec7fff426b}, 0x600f00, 0x3d3ca90, 0x3d3ca88
fixme:advapi:EventRegister {6e496e5e-d6c8-4522-930f-3556a6425109}, 0x600f00, 0x3d3cac8, 0x3d3cac0
fixme:advapi:EventRegister {491ae06a-ba67-462e-8bd6-e594116ead1d}, 0x600f00, 0x3d3cb00, 0x3d3caf8
fixme:advapi:EventRegister {2ec209be-090c-4504-b6d4-533067f18e57}, 0x600f00, 0x3d3cb38, 0x3d3cb30
 ___________________________________________ 
|                                           |
| Build ID:                   46733         |
| Perforce CL:              1184026         |
|___________________________________________|

------------------------------------------------------------
Total user memory:      2147483647 bytes - 2048.00 MB 
Total available memory: 2147483647 bytes - 2048.00 MB 
------------------------------------------------------------

arg0: fifa.exe

------------------------------------------------------------
MemoryFramework Initialization - set up heaps

  Loading: C:\Program Files\Origin Games\FIFA 13\memoryfw.ini
  Using embedded copy of file: C:\Program Files\Origin Games\FIFA 13\memoryfw.ini
  MemoryTracking heap disabled! 
------------------------------------------------------------
Available RAM before heaps:      2147483647 bytes - 2048.00 MB
Size used by heaps:                      0 bytes - 0.00 MB
Available RAM after heaps:       2147483647 bytes - 2048.00 MB
------------------------------------------------------------

Creating EA::Messaging::Server
Initializing EA Messaging system
PatchPath: patch.big
fixme:thread:SetThreadIdealProcessor (0x1b0): stub
fixme:thread:SetThreadIdealProcessor (0x1b4): stub
fixme:thread:SetThreadIdealProcessor (0x1b8): stub
fixme:thread:SetThreadIdealProcessor (0x1bc): stub
fixme:thread:SetThreadIdealProcessor (0x1c8): stub
fixme:thread:SetThreadIdealProcessor (0x1d0): stub
fixme:thread:SetThreadIdealProcessor (0x1d4): stub
fixme:thread:SetThreadIdealProcessor (0x1d8): stub
Preloading 1st big file
[Systems]datax.big not found, probably loose file build
[Systems]data0.big not found, probably loose file build
Loading 1st bigfile took 0 ms
~~~~~~~~~~~done preload
loading locale big file
~~~~~~~~~~~done loading locale big file
loading region big files
fixme:thread:SetThreadIdealProcessor (0x1dc): stub
IniLoad > test.ini nKeys[0]
IniLoad > user.ini nKeys[0]
fixme:thread:SetThreadIdealProcessor (0x1e4): stub
Changelist # for this build: 1184026



------------------------------------------------------------
Loading DLL modules. System Memory Before = 2097151k
------------------------------------------------------------

fixme:thread:SetThreadIdealProcessor (0x1e8): stub
fixme:thread:SetThreadIdealProcessor (0x1fc): stub
Before LoadDataArchives(1)
[Systems]data1.big not found, probably loose file build
WindowsMessageThread started
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
[Systems]data2.big not found, probably loose file build
[Systems]data3.big not found, probably loose file build
[Systems]data4.big not found, probably loose file build
[Systems]data5.big not found, probably loose file build
[Systems]data6.big not found, probably loose file build
[Systems]data7.big not found, probably loose file build
After LoadDataArchives(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x1716e118,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x720x32 @60! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x720x32 @0! (XRandR)

And I get the Error E000

---

### Post by DeathByDenim on 2013-06-24
It looks like FIFA 13 needs a bit of work to get going. See the WineHQ database:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=26732&iTestingId=74370](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26732&iTestingId=74370)
That link is for the demo, but I assume the actual game is similar. So, according to the link, you need to run these commands:
```
winetricks d3dx10 d3dx11_42 d3dx11_43 d3dx9 d3dx9_26 d3dx9_28 d3dx9_31 d3dx9_35 d3dx9_36 d3dx9_39 d3dx9_42 d3dx9_43 dinput vcrun2010
winecfg
```
Then go to Libraries tab. Select "dinput" in libraries list and set it to "Builtin (Wine)" and try again.

---

### Post by honzi97 on 2013-06-24
Thank you, it started! But it's stuck on start screen and the terminal says:
err:d3d:state_undefined Undefined state.

---

### Post by DeathByDenim on 2013-06-24
Well, glad you got closer. :)
 There was a P.S. in the link I send you earlier about the in-game menu not appearing:
> P.S. BTW, in-game menu in FIFA 13 doesn't appear in Wine > 1.5.9. This bug is since Wine 1.5.10 and happens in FIFA 12 too. So compile Wine 1.5.9 in separate folder and launch FIFA 13 only with this version.
 It sounds like that is happening to you as well.

In any case, you might want to try a different version of wine than the one that ships with Ubuntu. You can get the latest version directly from winehq.org here:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

I don't have the game myself though, so I can't test it for you.

---

### Post by honzi97 on 2013-06-26
I updated it but it's still the same. Should I try another program?

---

### Post by DeathByDenim on 2013-06-26
Well, there is still CrossOver. It's a commercial product, but it does come with a 14 days free trial.
It's untested for FIFA 13 though: [http://www.codeweavers.com/compatibility/browse/name/?app_id=10588](http://www.codeweavers.com/compatibility/browse/name/?app_id=10588)
I'm not sure it will fare any better than wine. Actually it's based on wine in the first place.

There is also PlayOnLinux ( [http://www.playonlinux.com](http://www.playonlinux.com) ), which might work and it's free. It's also based on wine though. It allows you to use a specific version of wine per game. So you might get it to work by specifically using version 1.5.9 which can run the demo.

I haven't used any of the above programs myself, so I don't know how to set them up, but they seem to have good instructions at least.

I'm afraid you're out of luck for FIFA 13, unless any of the above work for some reason.

---

### Post by honzi97 on 2013-06-27
Ok, I'm gonna try PlayOnLinux. How do I compile Wine 1.5.9 in separate folder?

---

### Post by DeathByDenim on 2013-06-27
I have no experience with PlayOnLinux, so I don't know if I can help you any further with that, but here is the documentation about that:
[http://www.playonlinux.com/en/dev-documentation-5.html](http://www.playonlinux.com/en/dev-documentation-5.html)
At the very bottom of the page it says:
```
POL_Wine_PrefixCreate "1.3.4"
```
So that's how you specify a specific version apparently. I doesn't seem like any compiling is necessary, so that's good.

Actually, you might want to ask on their forum to see if anybody managed to get FIFA 13 working.

---

