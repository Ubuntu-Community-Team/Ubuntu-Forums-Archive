---
title: "get-edid ERROR"
date: 2012-03-14
forum: Desktop Environments
---

### Post by jai1234 on 2012-03-14
I  installed read-edid in ubuntu VM ware machine. I couldn't get the proper output when I use 'get-edid' command. Output is given below:

###############################################
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 200
    VBE string at 0xc5a7a "V M ware, Inc. VBE support 2.0"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function unsupported
    Call successful

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function unsupported
    Call successful

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
##################################################3

Please help me.

---

