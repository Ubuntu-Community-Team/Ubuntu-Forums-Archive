---
title: "How to install ram?"
date: 2012-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Randymanme on 2012-01-21
I want to add 2 GBs of RAM to my computer [Dell OptiPlex GX740 AMD Athlon(tm) 64 2X Dual Core Processor 4400+, 2.3 GHz]. 

Please  see screenshot of "DDR2 Memory Overview" from computer manual.  It came  with 2 GBs [two one-GB modules, installed into bank A (DIMM1 and  DIMM2)].  At the same time I bought the computer, I bought two more GBs  of RAM and it came as a single, 2GB module.  The salesperson told me  that I should wait until I took the computer out of the box and  assertained that it worked before installing more RAM. I didn't decide  to install the 2 GB module until I'd decided to keep the computer.  

First  I just did what the salesperson said and put the 2GB module in DIMM3;  but that didn't work.  So I read the manual.  It says, 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
NOTICE: Do not install ECC memory modules. Doing so may cause the system not to boot or otherwise impact performance.
NOTE: Always install DDR2 memory modules in the order indicated on the system board.

The recommended memory configurations are:

    A pair of matched memory modules installed in connectors DIMM1 and DIMM2

or

    A memory module installed in connector DIMM1

or

    A pair of matched memory modules installed in connectors DIMM1 and  DIMM2 and another matched pair installed in connectors DIMM3 and DIMM4

Be  sure to install a single memory module in DIMM1, the connector closest  to the edge of the system board, before you install modules in the other  connectors.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

So  I took the pair of one-GB modules out of bank A (DIMM1 AND DIMM2 ) and  put them in bank B (DIMM3 AND DIMM4) and put the 2-GB module in DIMM1,  leaving DIMM2 empty.  When I ran the Windows memory diagnostic tool, it  said all was well.  But after an hour or so, all was not well.  LMDE  would only boot to a scrambled screen and Windows 7 kept going to the  blue screen and dumping physical memory, and system recovery disc  wouldn't work and system restore didn't work.  When I removed the 2-GB  module and returned the pair of one-GB modules to bank A, all is well  again.

But since I have 2-GB more of RAM, I want to use it.  Will someone advise me?  Any help would be much appreciated.  Thank you.

---

### Post by Randymanme on 2012-01-21
So to sum up this thread, it took me almost a couple of weeks to finally figure out (with the help of  **[The-Wizard]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=53292")** at Linux Mint forums) that the ram problem was the computer [Dell  OptiPlex GX740 AMD Athlon(tm) 64 2X Dual Core Processor 4400+, 2.3  GHz,  nVidia Quadro NVS 210S, 2GB, 750 GB hdd].

So I packed that baby up in the box it came in and took it back to where I bought it.  I exchanged it for an eMachines                             AMD Athlon(tm) II X2 220 Processor, 2.8 GHz, 3 GB, Geforce 6150SE nForce 430, 1 TB hdd.

So far I'm rather pleased with it.  Oneiric is flying strong for me now.:guitar:

---

