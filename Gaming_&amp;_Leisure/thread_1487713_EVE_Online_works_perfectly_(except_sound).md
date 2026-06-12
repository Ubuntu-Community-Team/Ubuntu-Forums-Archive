---
title: "EVE Online works perfectly (except sound)"
date: 2010-05-19
forum: Gaming &amp; Leisure
---

### Post by miickEe on 2010-05-19
Hey

I have recently upgraded to Ubuntu 10.04 and am loving it, a great release. I have installed the latest EVE Online Dominion, and running it through wine1.2. Everything works perfectly, I get no errors (yet), except the sound does not work. The sound works perfectly fine in other applications, and in the sound test in winecfg. Even more perplexing is that the sound did work when I first ran the game. Then it just stopped, and never came back.

I am using on board sound card, the motherboard is a Gigabyte MA74GMT-S2. I am running eve from the command line, and this is the output:
```

mike@mike:~/Downloads$ wine explorer /desktop=0,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x6002c 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xf39c5a0,0xf39ca78): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x6002c, 0x1381b8): stub
fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_draw:drawPrimitive Using software emulation because not all material properties could be tracked
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x6002c
fixme:heap:HeapSetInformation 0x8d9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x7006c 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xf39c550,0xf39ca78): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x7006c, 0x1382b8): stub
fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x7006c

```

Has anyone else had this issue? If so how did you fix it? What else should I be looking at to solve this issue? Suggestions would be greatly appreciated :)

---

