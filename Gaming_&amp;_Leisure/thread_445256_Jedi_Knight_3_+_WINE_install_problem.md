---
title: "Jedi Knight 3 + WINE install problem"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by Hobo Joe on 2007-05-15
I'm installing Jedi Knight 3 through WINE, but when it asks me to insert the next disc, it can't find it, what path should I put in so that it will find the proper file?

Here is the output of the terminal from start to finish:
```

joseph@Schoolroom:~$ wine /media/cdrom0/JediAcademy.exe
err:mmio:MMIO_ParseExtA No . in szFileName: "D:\\Install\\HOVER"
err:mmio:MMIO_ParseExtA No . in szFileName: "D:\\Install\\HOVER"
joseph@Schoolroom:~$ err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x20026
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

```

Hope someone can help... :(

EDIT:

Wait, I got it. I'm a retard. *slaps forehead*

---

### Post by kwr2k on 2010-05-06
How did you resolve that error?

---

