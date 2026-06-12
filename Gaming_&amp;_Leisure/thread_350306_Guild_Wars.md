---
title: "Guild Wars"
date: 2007-01-31
forum: Gaming &amp; Leisure
---

### Post by Kat of Zion on 2007-01-31
I know that many may chide me with "silly gamer, Guild Wars is for Windows" or something but I really wanted to play it and IM not willing to go back to Windows ever.  Now I did install the game but Wine did not seem to like this at all.  I know that it seems Edgy is version that has this error (unlike Dapper Drake).  

The error I get is this:

```
*--> Crash <--*
Exception: c0000005 
Memory at address 8000010c could not be read
App: Gw.exe
ProgramId: 1
Build: 20703
When: 1/31/2007 09:52:19
Flags: 0

*--> System <--*
Name: leopardess
IpAddr: 127.0.1.1
Processors: 1 [AuthenticAMD:15:4:2]
OSVersion: 5.1

*--> Thread 0xfffffffe <--*
eax=00000015 ebx=00000000 ecx=800000f8 edx=00000000 esi=800000f8 edi=00000000
eip=701069b2 esp=7c6d62cc ebp=7c6d630c
cs=210282 ss=0073 ds=007b es=007b fs=007b gs=0033 efl=0000003b


*--> Code <--*
70106992  8946348b c6893530 d014705e c333c089 .F4...50..p^.3..
701069A2  41048901 8bc1c356 8bf1ff15 04e11470 A......V.......p
701069B2  3b46140f 849e4f00 0083c610 56ff156c ;F....O.....V..l
701069C2  e014705e c35733c0 8d791089 41088941 ..p^.W3..y..A..A
701069D2  0c8939c7 41040400 0000abab abab8bc1 ..9.A...........
701069E2  5fc3e8a3 a8ffff83 3d04d014 70007538 _.......=...p.u8

*--> Trace <--*
Pc:701069b2 Fr:7c6d630c Rt:7bc37f45 Arg:70100000 00000001 00000000 00053000 

*--> Stack <--*
7C6D62CC  00000184 701067e6 00000000 70101dc3 .....g.p.......p
7C6D62DC  035bd228 00000000 7bc796a8 00000000 (.[........{....
7C6D62EC  00000000 00000000 7c6d62dc 7c6d5e40 .........bm|@^m|
7C6D62FC  7c6d6a28 7010a6dc 70146488 ffffffff (jm|...p.d.p....
7C6D630C  7c6d632c 7bc37f45 70100000 00000001 ,cm|E..{...p....
7C6D631C  00000000 00053000 00000188 7bc796a8 .....0.........{
7C6D632C  7c6d63dc 7bc3923c 70101ba1 70100000 .cm|<..{...p...p
7C6D633C  00000001 00000000 00000184 7c6d643c ............<dm|
7C6D634C  00000000 7c6d6400 00000005 00000000 .....dm|........
7C6D635C  03108e28 b7ed5e12 b7fcb99c 00000000 (....^..........
7C6D636C  00000001 035bd228 70101ba1 70100000 ....(.[....p...p
7C6D637C  00000000 bfffac00 03108d38 00000004 ........8.......
7C6D638C  00000040 bfffa000 00000000 7c6d63a0 @............cm|
7C6D639C  00000000 003a0043 0077005c 006e0069 ....C.:.\.w.i.n.
7C6D63AC  006f0064 00730077 0073005c 00730079 d.o.w.s.\.s.y.s.
7C6D63BC  00650074 0033006d 005c0032 00000000 t.e.m.3.2.\.....
7C6D63CC  00000000 7bc796a8 00000000 035bd228 .......{....(.[.
7C6D63DC  7c6d641c 7bc396dd 00000000 7c6d63f8 .dm|...{.....cm|
7C6D63EC  00000040 00000000 00000000 00000000 @...............
7C6D63FC  00000000 00000000 00000001 00000000 ................
7C6D640C  00000000 7bc796a8 00000000 7bc81184 .......{.......{
7C6D641C  7c6d644c 7bc3b5e7 7c6d643c 7bc28b31 Ldm|...{<dm|1..{
7C6D642C  7bc40bb3 003c003c 03108dd6 000a0008 ...{<.<.........
7C6D643C  035bd228 7b8ab6c0 03108d38 00000000 (.[....{8.......
7C6D644C  7c6d669c 7b8619fb 03108d38 00000000 .fm|...{8.......
7C6D645C  7c6d66b8 7c6d668c 03108d38 7b8ab6c0 .fm|.fm|8......{
7C6D646C  03108d38 7b8ab6c0 7c6d66c4 7c6d66b8 8......{.fm|.fm|
7C6D647C  00110000 00000000 03108d38 7c6d66b4 ........8....fm|
7C6D648C  00000000 b7ea5ff4 7c6d6500 7c6d65d0 ....._...em|.em|
7C6D649C  7c6d64b8 7c6d66e0 00000000 00000000 .dm|.fm|........
7C6D64AC  7b8ab6c0 0000000a 7c6d65d0 7c6d6608 ...{.....em|.fm|
7C6D64BC  b7ed75e4 00000184 7c6d65b0 00000014 .u.......em|....
7C6D64CC  7c6d65a4 0000002c 7c6d65f0 00027168 .em|,....em|hq..
7C6D64DC  0001a910 00078a30 7c6d65b0 00000000 ....0....em|....
7C6D64EC  7c6d6594 7c6d65f4 00000000 b7d9fb29 .em|.em|....)...
7C6D64FC  00000001 7b8ab6c0 0000000a 7c6d65d0 .......{.....em|
7C6D650C  7c6d6608 836764c0 84894faf 00000001 .fm|.dg..O......
7C6D651C  00000000 00000000 0000002d 00000011 ........-.......
7C6D652C  7eb48a0c 00000084 00000b68 7c6d6710 ...~....h....gm|
7C6D653C  0315e478 0315e878 7c6d65ec 7c6d6674 x...x....em|tfm|
7C6D654C  00000000 b7d9fb29 7c6d65a4 7bc36c20 ....)....em| l.{
7C6D655C  03080000 0000000e 7c6d6584 b7ed7271 .........em|qr..
7C6D656C  7c6d65e8 000e0000 7c004f76 7bc3579e .em|....vO.|.W.{
7C6D657C  0000000e 0000fdf2 7c6d662c 7c6d6694 ........,fm|.fm|
7C6D658C  00000000 b7d9fb29 7c6d65b0 b7d9f4dd ....)....em|....
7C6D659C  00000000 00000000 7c6d65f4 7bc796a8 .........em|...{
7C6D65AC  65f00000 7c6d6680 7bc38fe6 b7ed4974 ...e.fm|...{tI..
7C6D65BC  00000001 b7fcb3fc 00000000 7c6d66fc .............fm|
7C6D65CC  7c6d6a28 7bc2f440 00000001 7bc796a8 (jm|@..{.......{
7C6D65DC  65f3fddc 00000000 7c6d6680 b7ed4974 ...e.....fm|tI..
7C6D65EC  7c6d663c 7bc796a8 00000000 bfffabf8 <fm|...{........
7C6D65FC  7c6d662c 7bc4e0d6 b7fcb3fc 00000000 ,fm|...{........
7C6D660C  65f3fddc 0000000a 00000000 00000000 ...e............
7C6D661C  037f0000 7bc796a8 00000014 00000000 .......{........
7C6D662C  7c6d665c 7bc4e263 b7fcb3fc 00000000 \fm|c..{........
7C6D663C  65f3fddc 0000000a bfffac00 0000000a ...e............
7C6D664C  7b89450e 7bc796a8 00000000 bfffabf8 .E.{...{........
7C6D665C  7c6d668c 7bc4e751 bfffac00 00000014 .fm|Q..{........
7C6D666C  00000000 65f3fddc 0000000a 038ed6e0 .......e........
7C6D667C  00000002 7b8ab6c0 00000000 7c6d66b8 .......{.....fm|
7C6D668C  7c6d66cc 7b8ab6c0 bfffac00 7c6d66b8 .fm|...{.....fm|
7C6D669C  7c6d66cc 7b861c10 7c6d66b8 bfffac00 .fm|...{.fm|....
7C6D66AC  bfffabf8 7c6d66f0 7bc39c7d 00160014 .....fm|}..{....
7C6D66BC  bfffac00 7b8ab6c0 017079c0 0147cd14 .......{.yp...G.

*--> LogQueue <--*
(2) Sound failed to init

*--> DirectX Device Info <--*
VendorId    = 0x10de
DeviceId    = 0x0253
Version     = 6.14.0010.7174
Description = Direct3D HAL
Compat      = 0x00000001
VidMem      = 64 MB
```

Incidentally my video card is  an ATI Radeon Express 200M.
:frown:  :???:

---

### Post by der_joachim on 2007-01-31
Read Jarn's [guide]("http://ubuntuforums.org/showthread.php?t=283122") elsewhere in this forum. It mostly works and is well playable.

---

### Post by Kat of Zion on 2007-02-01
Update: That pretty much seemed to help.  I got everything working except that now instead of crashing I get the whole silly directx problem solved.  I have tried configuring wine's settings but I think its a dll that is missing or something.  

Vid card: ATI Radeon Xpress 200M

---

