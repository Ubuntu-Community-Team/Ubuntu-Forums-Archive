---
title: "America's Army 2.8 with Wine: installation problem"
date: 2007-03-05
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2007-03-05
Hello all,
   I'm trying my hardest to get America's Army 2.8.0 working in Edgy, since native Linux support died in AA2.5.  I've already tried Cedega, but according to their forums, Cedega's poor MSI support makes it impossible.  They also mentioned that it might work under wine.   

Wine gets farther than Cedega does, actually finishing the extraction of the installation files.  However, it progresses no further as it fails to run the installation wizard.  Immediately after extraction finishes, I'm greeted by [this image]("http://people.bu.edu/keithjr/AAerror.png").  

Here's the output from the console.  There are many things in there which make me feel like this isn't solvable but if anybody recognizes anything, I'd be much obliged.

```

fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:exec:SHELL_execute flags ignored: 0x00000580
fixme:advapi:LookupAccountNameW (null) L"keithjr" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"keithjr" 0x176e60 0x34f808 0x176e78 0x34f804 0x34f810 - stub
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7c660f90,0x614212,0x7c6610c4): stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:rpc:RPCRT4_OpenBinding failed to bind for interface {00020400-0000-0000-c000-000000000046}, 0.0
fixme:rpc:RpcImpersonateClient (0x713190): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2000000021
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x713190): stub
err:msi:ITERATE_Actions Execution halted, action L"IS_CheckForOld" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

```

Wine version:  0.9.30

---

### Post by pcjunkie on 2007-03-18
I wish I could do the same, I am fed up with this windows only horse manure......
Next they will tell us we have to upgrade to Vista just so D3D 10 can be used...

Enough!

Vista is Windows Blinds plus a touch of confetti and it costs $500 here.....

Grrrr hiss rant......

---

### Post by Motoxrdude on 2007-03-18
> **pcjunkie said:**
> I wish I could do the same, I am fed up with this windows only horse manure......
Next they will tell us we have to upgrade to Vista just so D3D 10 can be used...

Enough!

Vista is Windows Blinds plus a touch of confetti and it costs $500 here.....

Grrrr hiss rant......

Where do you live?

---

