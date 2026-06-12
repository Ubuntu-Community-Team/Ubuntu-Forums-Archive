---
title: "Cannot detect Dell RD1000"
date: 2010-02-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andremta on 2010-02-12
I'm using Ubuntu Server 9.10 x64 in a PowerEdge 2950 (2006) server with an internal RD1000 Data Cartridge.

My server is not detecting the RD1000, is it compatible?


> 
atenreiro@server:~$ sudo **cat /proc/scsi/scsi**

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: CD-ROM GCR-8240N Rev: 1.10
  Type:   CD-ROM                           ANSI  SCSI revision: 05

Host: scsi2 Channel: 00 Id: 08 Lun: 00
  Vendor: DP       Model: BACKPLANE        Rev: 1.00
  Type:   Enclosure                        ANSI  SCSI revision: 05

Host: scsi2 Channel: 02 Id: 00 Lun: 00
  Vendor: DELL     Model: PERC 5/i         Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 05

atenreiro@server:~$



---

### Post by andremta on 2010-02-13
Anyone was able to setup this DELL PowerVault RD1000 (Internal) with Ubuntu? 

I'm not sure if its compatible.

---

### Post by andremta on 2010-03-02
I willing to pay to someone, in order to help me to fix this problem!

---

