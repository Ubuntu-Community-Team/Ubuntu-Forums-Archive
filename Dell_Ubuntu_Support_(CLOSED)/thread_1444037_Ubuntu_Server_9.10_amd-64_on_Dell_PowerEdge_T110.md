---
title: "Ubuntu Server 9.10 amd-64 on Dell PowerEdge T110"
date: 2010-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by richard.zeng on 2010-03-31
We just bought a T110 server, and installed Ubuntu server. This server has a SAS 6/iR controller card, which provide RAID support.

After installation, everything else seems good, except we got some warning information:

ata_id[606]: HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:32'

ata_id[607]: HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:16'

ata_id[609]: HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:0'

ata_id[865]: HDIO_GET_IDENTITY failed for '/dev/sdc'

ata_id[864]: HDIO_GET_IDENTITY failed for '/dev/sda'

ata_id[887]: HDIO_GET_IDENTITY failed for '/dev/sdb'

As you can tell, we have three SATA hard drives connect to SAS 6/iR card. If we connect the SATA drive directly to SATA port on motherboard, the message disappeared.

Is it safe for us to continue without worrying about this message?

Thanks for any help.

---

### Post by jonnytabpni on 2010-05-17
Hi There,

Did you ever fix this issue? Does the latest Ubuntu 10.04 make those messages go away?

I'm about to purchase this server.

Even with the messages, does it cause any problems?

Thanks

---

