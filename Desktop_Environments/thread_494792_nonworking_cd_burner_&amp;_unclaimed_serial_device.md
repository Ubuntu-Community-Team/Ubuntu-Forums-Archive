---
title: "nonworking cd burner &amp; unclaimed serial device"
date: 2007-07-07
forum: Desktop Environments
---

### Post by h4mx0r on 2007-07-07
Got this gateway computer and don't exactly know model information about it, but my cd burner has been reported as not working by many burning applications. I have two drives one does stuff with dvds and other burns.  Here is lshw info about the working dvd one:

           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM LF-D311
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A123
                capabilities: removable audio dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

The burning drive however is not listed by lshw but after speaking with someone on irc channel that had same issue I noticed we both had similar listing in lshw:

        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0-efaf irq:10

This person reported that his burner worked in dapper and edgy however stopped working after he did a second upgrade to feisty. I have also experienced some cd burning difficulties with feisty and was wondering if anyone had more information on the matter.

---

