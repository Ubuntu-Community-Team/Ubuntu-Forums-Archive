---
title: "tring to install AA 2.8"
date: 2006-12-25
forum: Gaming &amp; Leisure
---

### Post by lexus_is250_awd on 2006-12-25
Can anybody tell me why I'm getting this error?
I'm tring to install AA 2.8 and get this error:

@Ubuntu:~$ wine ~/Downloads/Americas_Army/AA2.8/AA28FullInstaller_Generic.exe
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:exec:SHELL_execute flags ignored: 0x00000580
fixme:advapi:LookupAccountNameW (null) L"guido" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"guido" 0x178488 0x34f808 0x1784a0 0x34f804 0x34f810 - stub
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7c3aff30,0x614212,0x7c3b0064): stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:rpc:RPCRT4_OpenBinding failed to bind for interface {00020400-0000-0000-c000-000000000046}, 0.0
fixme:rpc:RpcImpersonateClient (0x1cdf70): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2000000021
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x1cdf70): stub
err:msi:ITERATE_Actions Execution halted, action L"IS_CheckForOld" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

I'm typing this to install: wine ~/Downloads/Americas_Army/AA2.8/AA28FullInstaller_Generic.exe

install window pops up and it shows it's extracting files then window disappears and another windows pops up saying: The wizard was interrupted before AMerica's Army could be completely installed. Your system has not been modified. To complete installation at another time, please run setup again.

---

### Post by medicineman24 on 2007-05-27
I have the same problem: 

matt@matt-desktop:~/Downloads$ wine AA28FullInstaller_FileShack.exe
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:exec:SHELL_execute flags ignored: 0x00000580
fixme:advapi:LookupAccountNameW (null) L"matt" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"matt" 0x177b20 0x34f808 0x1730e0 0x34f804 0x34f810 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:ole:TMStubImpl_Invoke invoke call failed with exception 0xc0000005 (-1073741819)
err:ole:xCall RpcChannelBuffer SendReceive failed, c0000005
fixme:rpc:RpcImpersonateClient (0x1ceae8): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2000000021
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x1ceae8): stub
err:msi:ITERATE_Actions Execution halted, action L"IS_CheckForOld" returned 1603

Help Anyone? Maybe ATI driver? (Noob)

---

