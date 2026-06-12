---
title: "Paratext Installation Problem"
date: 2006-09-27
forum: Desktop Environments
---

### Post by zedlander on 2006-09-27
Hello,
I'm trying to install the Paratext program on Linux.  It's only
available to some people, so you can't try it yourself, but it's
running into a problem with the MSI.  It runs the GUI, and gets most of
the way through before saying that the wizard was interrupted before
the installation could be completed.  It's using the InstallShield
Wizard.  Here's the output from the terminal:

```
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program
Files\\Common Files\\InstallShield\\Driver\\8\\Intel 32\\IDriver.exe"
-> L"c:\\Program Files\\Common Files\\InstallShield\\Driver\\8\\Intel
32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files
as well
fixme:msi:ACTION_HandleStandardAction unhandled standard action
L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action
L"RemoveFolders"
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF
header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7d7910f4,0x3f4212,0x7d7911f8): stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to
finish
err:rpc:RPCRT4_OpenBinding failed to bind for interface
{00020400-0000-0000-c000-000000000046}, 0.0
fixme:rpc:RpcImpersonateClient (0x62af10): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment,
should have been 0x1000000011
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x62af10): stub
fixme:rpc:RpcImpersonateClient (0x62b0d0): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment,
should have been 0x1000000011
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
err:rpc:RPCRT4_OpenBinding failed to bind for interface
{00020400-0000-0000-c000-000000000046}, 0.0
fixme:rpc:RpcRevertToSelfEx (0x62b0d0): stub
err:msi:ITERATE_Actions Execution halted, action
L"SetupAllExistingRegistrationProperties" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^(nil),
MgrTypeUuid == (null), WaitForCallsToComplete == 0): stub
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

```

Any help would be appreciated.

Thanks!
Trevor

---

