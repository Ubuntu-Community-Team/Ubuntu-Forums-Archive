---
title: "office 2003"
date: 2009-03-14
forum: General Help
---

### Post by sandyd on 2009-03-14
running the office 2003 installer in the latest version of WINE gives me this.

```

starangyl@studenthotspot:/opt2/OFFICE$ WINEPREFIX=/opt2/office2003/ wine SETUP
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:CheckTokenMembership ((nil) 0x13a198 0x326d3c) stub!
fixme:advapi:LookupAccountNameW (null) L"starangyl" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"starangyl" 0x13f408 0x33f80c 0x13eb70 0x33f810 0x33f804 - stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:CheckTokenMembership ((nil) 0xf4fc98 0x8ce0c8) stub!
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 76 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msid1ec.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7ee4eb78 "handle.c: MSI_object_cs" wait timed out in thread 001a, blocked by 003a, retrying (60 sec)
wine: Critical section 7ee4eb78 wait failed at address 0x7bc3c090 (thread 001a), starting debugger...
Unhandled exception: wait failed on critical section 0x7ee4eb78
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3c090
Process of pid=0019 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000c 
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000017 
    00000018    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'


```using WineHQ resipostries
running this in , as you see in a new, seperate bottle b/c/ i don't feel like harming my main bottle. 

any help ?

---

### Post by studavis on 2009-04-02
Did you ever get a solution? I'm having the same problem. Now running 8.04 with fresh install Wine 1.1.18.

---

