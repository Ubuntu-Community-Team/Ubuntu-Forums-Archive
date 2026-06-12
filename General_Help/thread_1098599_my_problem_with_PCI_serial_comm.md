---
title: "my problem with PCI serial comm"
date: 2009-03-17
forum: General Help
---

### Post by lplq on 2009-03-17
Hello

i have a problem with the new pci for serial comm to run CCcam server

anyway i tried for along time and a lot of commands but it's not work only the comm which it in the motherboard.

i will show you 
root@ammar-Linux:/home/ammar# ls -al /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2009-03-16 01:04 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-03-16 00:22 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-03-16 00:22 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-03-16 00:22 /dev/ttyS3
crw-rw---- 1 root dialout 4, 68 2009-03-16 00:22 /dev/ttyS4


root@ammar-Linux:/# setserial /dev/ttyS1 -a
/dev/ttyS1, Line 1, UART: 8250, Port: 0x1028, IRQ: 16
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

root@ammar-Linux:/# setserial /dev/ttyS2 -a
/dev/ttyS2, Line 2, UART: 8250, Port: 0x1040, IRQ: 16
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

and this is the configurs
PHOENIX READER PATH : /dev/ttyS0
SMARTCARD CLOCK FREQUENCY: /dev/ttyS0 6000000
CAMKEY: /dev/ttyS0 00 00 00 00 00 00 00 00
CAMDATA: /dev/ttyS0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
TRY ALL CHIDS : /dev/ttyS0

PHOENIX READER PATH : /dev/ttyS1
SMARTCARD CLOCK FREQUENCY: /dev/ttyS1 6000000
CAMKEY: /dev/ttyS1 00 00 00 00 00 00 00 00
CAMDATA: /dev/ttyS1 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
TRY ALL CHIDS : /dev/ttyS1

PHOENIX READER PATH : /dev/ttyS2
SMARTCARD CLOCK FREQUENCY: /dev/ttyS2 6000000
CAMKEY: /dev/ttyS2 00 00 00 00 00 00 00 00
CAMDATA: /dev/ttyS2 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
TRY ALL CHIDS : /dev/ttyS2

this is for comm in the motherboard , it's work and the other is dosen't
card reader /dev/ttyS0
handled 70(62) ecms and 2(2) emms
Irdeto card
Caid 603 ACS 606
Cardserial 4110226710U8340000A (25a878)
Provider 00 003400
Provider 01 003400
Provider 02 003400
Provider 03 003400
Chid EFFC - date 0xcc7 valid 0x0
Chid F000 - date 0xcc7 valid 0xfe
Chid 03E7 - date 0xcc7 valid 0xfe

please help me
thanks alot

---

### Post by lplq on 2009-03-17
no one can help ??

please

---

