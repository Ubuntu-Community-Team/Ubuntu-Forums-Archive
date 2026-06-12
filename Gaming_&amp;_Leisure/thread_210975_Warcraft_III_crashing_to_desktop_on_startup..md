---
title: "Warcraft III crashing to desktop on startup."
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by bocmaxima on 2006-07-07
It worked perfectly on my last install of Wine/Ubuntu. Heres the error I get from running it from the terminal.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f4a4,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  392
  Current serial number in output stream:  392

```

Something fixable or should I just do a complete reinstall of Ubuntu?

---

### Post by vem0m on 2006-07-07
hmmmmm u tryed going to terminal and using winecfg? and checking those settings?

---

### Post by bocmaxima on 2006-07-07
> **vem0m said:**
> hmmmmm u tryed going to terminal and using winecfg? and checking those settings?

I dunno what to change really, but I tried a bunch of different configurations to no avail.

---

### Post by vem0m on 2006-07-07
hmmmmm might be a bug within X as u have to realize things updated don't always work as good as the old version u might try reinstalling wine and then don't forget to use 'winecfg' afterwords if that however fails u might try using CedegaCVS or even the paid version for a month just to get the engine then continue using it without paying only thing lacking would be updates....

---

### Post by bocmaxima on 2006-07-08
> **vem0m said:**
> hmmmmm might be a bug within X as u have to realize things updated don't always work as good as the old version u might try reinstalling wine and then don't forget to use 'winecfg' afterwords if that however fails u might try using CedegaCVS or even the paid version for a month just to get the engine then continue using it without paying only thing lacking would be updates....

I tried reinstalling my OS, as well as Wine, tried to play it under the old version from the guide and got the above error, upgraded to the newest and got

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f4a4,0x00000000), stub!
bocmaxima@Serenity:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c95c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8cd84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8cfc8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8d058,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
epoll_ctl: Operation not permitted
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fdba478) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fdb9e20)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x7fda4af8)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x7fda4af8)->()
fixme:quartz:PullPin_EndFlush (0x7fda4af8)->()
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f4b0,0x00000000), stub!

```

I also tried CVSCedega and it wont play it. I dont want to shell out 15 bucks to find that Cedega doesnt run it either.

The real problem is that when I first installed Ubuntu and Wine, the game freakin worked perfectly, how does it go from wotking on my sytem flawless, to getting fatal errors, I didnt do anything different I dont believe.

Any help would be appreciated.

---

### Post by bocmaxima on 2006-07-08
It ran for a second and then I got this monster.

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f4a4,0x00000000), stub!
bocmaxima@Serenity:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c95c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8cd84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8cfc8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8d058,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
epoll_ctl: Operation not permitted
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fdba6e0) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fdba088)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x7fda4d60)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x7fda4d60)->()
fixme:quartz:PullPin_EndFlush (0x7fda4d60)->()
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8f4b0,0x00000000), stub!
fixme:wave:DSD_CreateSecondaryBuffer (0x7fdb9a50,0x7b2b89bc,180e0,0,0x7fdc0994,0x7fda48dc,0x7fdc0970): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd5fb10,0x7b2b89bc,180e0,0,0x7fdc0994,0x7fd5f744,0x7fdc0970): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:imm:ImmGetOpenStatus (0x7fda6088): semi-stub
fixme:imm:ImmReleaseContext (0x40028, 0x7fda6088): stub
fixme:imm:ImmGetOpenStatus (0x7fda6088): semi-stub
fixme:imm:ImmReleaseContext (0x40028, 0x7fda6088): stub
fixme:imm:ImmGetOpenStatus (0x7fda6088): semi-stub
fixme:imm:ImmReleaseContext (0x40028, 0x7fda6088): stub
fixme:imm:ImmGetOpenStatus (0x7fda6088): semi-stub
fixme:imm:ImmReleaseContext (0x40028, 0x7fda6088): stub
fixme:imm:ImmSetConversionStatus (0x7fda6088, 1, 0): stub
fixme:imm:ImmReleaseContext (0x40028, 0x7fda6088): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fdc0948
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fdc0948
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c1b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c820,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8c8b0,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)
epoll_ctl: Operation not permitted
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:quartz:CreateRenderingWindow Unable to register window 582
err:quartz:GraphBuilder_Render Unable to create filter (80004005), trying next one
fixme:quartz:DllGetClassObject {07167665-5011-11cf-bf33-00aa0055595a}: no class found.
err:quartz:GraphBuilder_Render Unable to create filter (80040154), trying next one
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x7fdc9758)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x7fdc9758)->()
fixme:quartz:PullPin_EndFlush (0x7fdc9758)->()
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
[FAIL] pivw->put_Owner(NULL) = -2147467262fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x50028,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x50028,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fd808b0, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8ed08,0x00000000), stub!
wine: Unhandled page fault on read access to 0x000000ac at address 0x6f0b6805 (thread 000e), starting debugger...
WineDbg starting on pid 0xd
Unhandled exception: page fault on read access to 0x000000ac in 32-bit code (0x6f0b6805).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:6f0b6805 ESP:7fb8e6ac EBP:7fb8e6b4 EFLAGS:00210212(   - 00      - RIA1)
 EAX:7fb8e6c8 EBX:7fb8ed60 ECX:0000000a EDX:7fb8ed60
 ESI:000000ac EDI:7fb8e6c8
Stack dump:
0x7fb8e6ac:  79440f3c 79440f30 7fb8e6f0 6f0b5917
0x7fb8e6bc:  7fb8e6c8 79440f3c 79440f30 7fb8e734
0x7fb8e6cc:  1502072b 00000068 00000005 150208b2
0x7fb8e6dc:  41729cc5 79440000 6f69157c 7ff8959d
0x7fb8e6ec:  00bd3eb2 7fb8e75c 6f04b687 7fb8e708
0x7fb8e6fc:  79440f3c 79440f30 00000000 7ff8959d
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x6f0b6805 in game (+0xb6805) (0x6f0b6805)
  2 0x6f0b5917 in game (+0xb5917) (0x6f0b5917)
  3 0x6f04b687 in game (+0x4b687) (0x6f04b687)
  4 0x6f04c2fa in game (+0x4c2fa) (0x6f04c2fa)
  5 0x6f04bd98 in game (+0x4bd98) (0x6f04bd98)
  6 0x6f032b5e in game (+0x32b5e) (0x6f032b5e)
  7 0x6f0328dc in game (+0x328dc) (0x6f0328dc)
  8 0x6f0211c7 in game (+0x211c7) (0x6f0211c7)
  9 0x6f020dae in game (+0x20dae) (0x6f020dae)
  10 0x6f020d3a in game (+0x20d3a) (0x6f020d3a)
  11 0x6f020a62 in game (+0x20a62) (0x6f020a62)
  12 0x6f0437b7 in game (+0x437b7) (0x6f0437b7)
  13 0x6f23734b in game (+0x23734b) (0x6f23734b)
  14 0x6f019a12 in game (+0x19a12) (0x6f019a12)
  15 0x6f3ee6a0 in game (+0x3ee6a0) (0x6f3ee6a0)
  16 0x6f3ee1f5 in game (+0x3ee1f5) (0x6f3ee1f5)
  17 0x6f407e45 in game (+0x407e45) (0x6f407e45)
  18 0x6f406f74 in game (+0x406f74) (0x6f406f74)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature C63A16CD in module war3
  19 0x00439219 in war3 (+0x39219) (0x00439219)
  20 0x0043d733 in war3 (+0x3d733) (0x0043d733)
  21 0x0043d611 in war3 (+0x3d611) (0x0043d611)
  22 0x00401148 in war3 (+0x1148) (0x00401148)
  23 0x7fb8fef8 (0x7fb8fef8)
  24 0x00468090 in war3 (+0x68090) (0x00468090)
  25 0x7fc3b94f in kernel32 (+0x4b94f) (0x7fc3b94f)
  26 0xb7f50443 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f50443)
0x6f0b6805: repe movsl  (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (102 modules)
PE      0x00400000-004ac000     Export          war3
PE      0x15000000-15050000     Deferred        storm
PE      0x21100000-2115f000     Deferred        mss32
PE      0x22600000-22616000     Deferred        mssfast.m3d
PE      0x22700000-22717000     Deferred        mssdolby.m3d
PE      0x22c00000-22c18000     Deferred        msseax2.m3d
PE      0x24600000-24611000     Deferred        reverb3.flt
PE      0x26f00000-26f2a000     Deferred        mp3dec.asi
PE      0x60000000-6005d000     Deferred        ijl15
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x6f000000-6f78f000     Export          game
ELF     0x78af3000-78b40000     Deferred        rpcrt4<elf>
  \-PE  0x78b00000-78b40000     \               rpcrt4
ELF     0x7ad97000-7ade0000     Deferred        dsound<elf>
  \-PE  0x7ada0000-7ade0000     \               dsound
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7c85c000-7c870000     Deferred        mswsock<elf>
  \-PE  0x7c860000-7c870000     \               mswsock
ELF     0x7e05a000-7e0d0000     Deferred        libglu.so.1
ELF     0x7e137000-7e1b0000     Deferred        opengl32<elf>
  \-PE  0x7e150000-7e1b0000     \               opengl32
ELF     0x7e52b000-7e540000     Deferred        midimap<elf>
  \-PE  0x7e530000-7e540000     \               midimap
ELF     0x7e67e000-7e696000     Deferred        msacm32<elf>
  \-PE  0x7e680000-7e696000     \               msacm32
ELF     0x7e696000-7e6d2000     Deferred        wineoss<elf>
  \-PE  0x7e6a0000-7e6d2000     \               wineoss
ELF     0x7e6d2000-7e71e000     Deferred        libgcrypt.so.11
ELF     0x7e71e000-7e72e000     Deferred        libtasn1.so.2
ELF     0x7e72e000-7e75b000     Deferred        libcrypt.so.1
ELF     0x7e76a000-7e7d3000     Deferred        libgnutls.so.12
ELF     0x7e7d3000-7e800000     Deferred        libcups.so.2
ELF     0x7e869000-7e89a000     Deferred        uxtheme<elf>
  \-PE  0x7e870000-7e89a000     \               uxtheme
ELF     0x7e89a000-7e8b6000     Deferred        imm32<elf>
  \-PE  0x7e8a0000-7e8b6000     \               imm32
ELF     0x7e8b6000-7f078000     Deferred        libglcore.so.1
ELF     0x7f078000-7f0fd000     Deferred        libgl.so.1
ELF     0x7f0fd000-7f1e3000     Deferred        libx11.so.6
ELF     0x7f1e3000-7f1f0000     Deferred        libxext.so.6
ELF     0x7f1f0000-7f208000     Deferred        libice.so.6
ELF     0x7f208000-7f28b000     Deferred        winex11<elf>
  \-PE  0x7f220000-7f28b000     \               winex11
ELF     0x7f28b000-7f2aa000     Deferred        libexpat.so.1
ELF     0x7f2aa000-7f2d8000     Deferred        libfontconfig.so.1
ELF     0x7f2d8000-7f2ec000     Deferred        libz.so.1
ELF     0x7f2ec000-7f355000     Deferred        libfreetype.so.6
ELF     0x7f355000-7f374000     Deferred        iphlpapi<elf>
  \-PE  0x7f360000-7f374000     \               iphlpapi
ELF     0x7f374000-7f39e000     Deferred        ws2_32<elf>
  \-PE  0x7f380000-7f39e000     \               ws2_32
ELF     0x7f39e000-7f3b8000     Deferred        wsock32<elf>
  \-PE  0x7f3a0000-7f3b8000     \               wsock32
ELF     0x7f3b8000-7f3cc000     Deferred        lz32<elf>
  \-PE  0x7f3c0000-7f3cc000     \               lz32
ELF     0x7f3cc000-7f3e5000     Deferred        version<elf>
  \-PE  0x7f3d0000-7f3e5000     \               version
ELF     0x7f3e5000-7f446000     Deferred        msvcrt<elf>
  \-PE  0x7f3f0000-7f446000     \               msvcrt
ELF     0x7f446000-7f4ce000     Deferred        winmm<elf>
  \-PE  0x7f450000-7f4ce000     \               winmm
ELF     0x7f4ce000-7f4fd000     Deferred        winspool<elf>
  \-PE  0x7f4e0000-7f4fd000     \               winspool
ELF     0x7f4fd000-7f5bf000     Deferred        comctl32<elf>
  \-PE  0x7f510000-7f5bf000     \               comctl32
ELF     0x7f5bf000-7f615000     Deferred        shlwapi<elf>
  \-PE  0x7f5d0000-7f615000     \               shlwapi
ELF     0x7f615000-7f6ec000     Deferred        shell32<elf>
  \-PE  0x7f630000-7f6ec000     \               shell32
ELF     0x7f6ec000-7f787000     Deferred        comdlg32<elf>
  \-PE  0x7f6f0000-7f787000     \               comdlg32
ELF     0x7f787000-7f7c8000     Deferred        advapi32<elf>
  \-PE  0x7f790000-7f7c8000     \               advapi32
ELF     0x7f89d000-7f94e000     Deferred        gdi32<elf>
  \-PE  0x7f8b0000-7f94e000     \               gdi32
ELF     0x7f94e000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb93000-7fb9c000     Deferred        libxcursor.so.1
ELF     0x7fbcf000-7fcd0000     Export          kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fcdb000     Deferred        libxrender.so.1
ELF     0x7fcdb000-7fce0000     Deferred        libxxf86vm.so.1
ELF     0x7fce2000-7fce6000     Deferred        libgpg-error.so.0
ELF     0x7fce6000-7fcf0000     Deferred        libgcc_s.so.1
ELF     0x7fe00000-7fe04000     Deferred        libxfixes.so.3
ELF     0x7fe04000-7fe0e000     Deferred        libnss_files.so.2
ELF     0x7fe0e000-7fe17000     Deferred        libnss_nis.so.2
ELF     0x7fe17000-7fe2c000     Deferred        libnsl.so.1
ELF     0x7fe2c000-7fe35000     Deferred        libnss_compat.so.2
ELF     0x7fe37000-7fe3c000     Deferred        libxxf86dga.so.1
ELF     0x7fe3c000-7fe44000     Deferred        libsm.so.6
ELF     0x7fe48000-7fe6a000     Deferred        libm.so.6
ELF     0x7fe6a000-7ff62000     Deferred        libwine_unicode.so.1
ELF     0x7ff62000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff70000-7ffe0000     \               ntdll
ELF     0xb7df0000-b7df2000     Deferred        libnvidia-tls.so.1
ELF     0xb7df8000-b7dfb000     Deferred        libdl.so.2
ELF     0xb7dfb000-b7f2a000     Deferred        libc.so.6
ELF     0xb7f2a000-b7f3c000     Deferred        libpthread.so.0
ELF     0xb7f3c000-b7f3f000     Deferred        libxau.so.6
ELF     0xb7f4b000-b7f65000     Export          libwine.so.1
ELF     0xb7f68000-b7f7e000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000d (D) C:\Program Files\Warcraft III\War3.exe
        00000027   15
        00000025    0
        00000024    0
        00000021    0
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        00000019    0
        00000018   15
        00000015   15
        00000012    0
        00000011    0
        00000010    1
        0000000e    0 <==
0000000a
        0000000b    0

```

This is crazy, why was it working perfectly last week?

---

### Post by vem0m on 2006-07-08
seems to be a problem with X11 i have pmed u for contact info get with me so i can help u one on one

---

