---
title: "OpenOffice 1.1.2 Calc crash"
date: 2004-12-02
forum: Desktop Environments
---

### Post by mpfleger on 2004-12-02
Hi all.

Sorry if this is addressed elsewhere; I did a pretty thorough bit of digging around and came up empty =/

I was hoping someone could replicate this problem before I file a bug report, and that someone could help me identify who to file the report with.  I'm running the Warty PPC release on an iBook, and the problem relates to the hex2bin() function in OO Calc.

I put any value in a cell (27 in B2 for example) and then in cell C3 (in this example) enter the following:
=hex2bin(B2;8)

I get either a unrecoverable error or an outright crash.  Anyone else able to replicate this behaviour on PPC or other architectures?

Thanks in advance,
-m

---

