---
title: "DVD burn problems"
date: 2005-12-11
forum: General Help
---

### Post by justUsing on 2005-12-11
Since upgrading from Hoary to Breezy I have been unable to burn
DVD. This was, i guess, partly due to buying the wrong media (DVD+R) that was too new for my old burner.
However, i got a windows-using buddy to upgrade the firmware on my LITE-ON 1693S so that should work now.

I still can't get k3b or gnomebaker to work, however. They bail out after a short while.

So, i got 3kb to make an iso-image instead, thinking that it might
be easier then, but no such luck :( 

Here's the invocation of dvdrecord with errors:

----------------------------------------------------------------------------
<deleted>@Large:~/dvdbak$ sudo dvdrecord speed=1 -dao dev=/dev/hdg dwn.iso
dvdrtools v0.2.1
Portions (C) 2002-2005 Ark Linux <bero@arklinux.org>
This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program; see the file COPYING.  If not, write to the Free Software
Foundation, 59 Temple Place, Suite 330, Boston, MA 02111-1307, USA.
Based on:
Cdrecord 1.11a15 (i386-pc-linux-gnu) Copyright (C) 1995-2001 J\uffffrg Schilling
scsidev: '/dev/hdg'
devname: '/dev/hdg'
scsibus: -2 target: -2 lun: -2
Scanning device, b=6
Linux sg driver version: 3.5.27
Using libscg version 'bero-0.5a'
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitransp.c     1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SOHW-1693S'
Revision       : 'KS0B'
Device seems to be: Generic mmc2 DVD.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Starting to write CD/DVD at speed 1 in write mode for single session.
Last chance to quit, starting real write in 0 seconds. Operation starts.
trackno=0
dvdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 21 A4 F6 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (logical block address out of range) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.003s timeout 200s
write track data: error after 0 bytes
Sense Bytes: 70 00 00 00 00 00 00 0A 00 00 00 00 00 00 00 00 00 00
<deleted>@Large:~/dvdbak$
--------------------------------------------------------------------------------------

Can any of you make sense of this? What am i doing wrong?

Kind regards and humanity to you all.

---

### Post by sapo on 2005-12-11
I m with kinda of the same problem here.. i lost 2 cds yesterday trying to burn.

it gave me an mkisof exited with error code 1

In k3b and gnombaker, none worked.

I NEVER had problems with cd burning when using hoary, but in my first breezy install it was working.. i think that it stopped after i bought a new sata hd.

anyone have any clues?

---

