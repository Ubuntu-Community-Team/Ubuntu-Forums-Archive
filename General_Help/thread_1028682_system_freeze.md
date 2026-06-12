---
title: "system freeze"
date: 2009-01-02
forum: General Help
---

### Post by the-fang on 2009-01-02
sorry for my bad english

i use 8.10 and i have a problem. my system freezes quite often. i can't do anything, even switch to another console. the following is from my /var/log/sys

```
Jan  2 22:11:19 SES1 kernel: [10215.104830] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:11:19 SES1 kernel: [10215.104844] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:11:19 SES1 kernel: [10215.104845]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:11:19 SES1 kernel: [10215.104847]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:11:19 SES1 kernel: [10215.104851] ata5.00: status: { DRDY }
Jan  2 22:11:19 SES1 kernel: [10215.104871] ata5: soft resetting link
Jan  2 22:11:19 SES1 kernel: [10215.293528] ata5.00: configured for UDMA/33
Jan  2 22:11:19 SES1 kernel: [10215.309526] ata5.01: configured for UDMA/33
Jan  2 22:11:19 SES1 kernel: [10215.309541] ata5: EH complete
Jan  2 22:11:49 SES1 kernel: [10245.308369] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:11:49 SES1 kernel: [10245.308382] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:11:49 SES1 kernel: [10245.308387]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:11:49 SES1 kernel: [10245.308393]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:11:49 SES1 kernel: [10245.308405] ata5.00: status: { DRDY }
Jan  2 22:11:49 SES1 kernel: [10245.308425] ata5: soft resetting link
Jan  2 22:11:49 SES1 kernel: [10245.497524] ata5.00: configured for UDMA/33
Jan  2 22:11:49 SES1 kernel: [10245.513524] ata5.01: configured for UDMA/33
Jan  2 22:11:49 SES1 kernel: [10245.513538] ata5: EH complete
Jan  2 22:12:19 SES1 kernel: [10275.513040] ata5.00: limiting speed to UDMA/25:PIO4
Jan  2 22:12:19 SES1 kernel: [10275.513048] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:12:19 SES1 kernel: [10275.513059] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:12:19 SES1 kernel: [10275.513060]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:12:19 SES1 kernel: [10275.513062]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:12:19 SES1 kernel: [10275.513066] ata5.00: status: { DRDY }
Jan  2 22:12:19 SES1 kernel: [10275.513087] ata5: soft resetting link
Jan  2 22:12:20 SES1 kernel: [10275.701528] ata5.00: configured for UDMA/25
Jan  2 22:12:20 SES1 kernel: [10275.717524] ata5.01: configured for UDMA/33
Jan  2 22:12:20 SES1 kernel: [10275.717547] ata5: EH complete
Jan  2 22:12:50 SES1 kernel: [10305.717038] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:12:50 SES1 kernel: [10305.717053] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan  2 22:12:50 SES1 kernel: [10305.717059]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:12:50 SES1 kernel: [10305.717067]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:12:50 SES1 kernel: [10305.717078] ata5.01: status: { DRDY }
Jan  2 22:12:50 SES1 kernel: [10305.717099] ata5: soft resetting link
Jan  2 22:12:50 SES1 kernel: [10305.905754] ata5.00: configured for UDMA/25
Jan  2 22:12:50 SES1 kernel: [10305.920562] ata5.01: configured for UDMA/33
Jan  2 22:12:50 SES1 kernel: [10305.920578] ata5: EH complete
Jan  2 22:13:20 SES1 kernel: [10335.921039] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:13:20 SES1 kernel: [10335.921052] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:13:20 SES1 kernel: [10335.921057]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:13:20 SES1 kernel: [10335.921066]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:13:20 SES1 kernel: [10335.921077] ata5.00: status: { DRDY }
Jan  2 22:13:20 SES1 kernel: [10335.921097] ata5: soft resetting link
Jan  2 22:13:20 SES1 kernel: [10336.108696] ata5.00: configured for UDMA/25
Jan  2 22:13:20 SES1 kernel: [10336.125521] ata5.01: configured for UDMA/33
Jan  2 22:13:20 SES1 kernel: [10336.125536] ata5: EH complete
Jan  2 22:13:50 SES1 kernel: [10366.125036] ata5.00: limiting speed to PIO4
Jan  2 22:13:50 SES1 kernel: [10366.125045] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:13:50 SES1 kernel: [10366.125055] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:13:50 SES1 kernel: [10366.125056]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:13:50 SES1 kernel: [10366.125058]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:13:50 SES1 kernel: [10366.125062] ata5.00: status: { DRDY }
Jan  2 22:13:50 SES1 kernel: [10366.125082] ata5: soft resetting link
Jan  2 22:13:50 SES1 kernel: [10366.313458] ata5.00: configured for PIO4
Jan  2 22:13:50 SES1 kernel: [10366.329523] ata5.01: configured for UDMA/33
Jan  2 22:13:50 SES1 kernel: [10366.329536] ata5: EH complete
Jan  2 22:14:20 SES1 kernel: [10396.329037] ata5.00: limiting speed to PIO3
Jan  2 22:14:20 SES1 kernel: [10396.329046] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:14:20 SES1 kernel: [10396.329060] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:14:20 SES1 kernel: [10396.329061]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:14:20 SES1 kernel: [10396.329062]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:14:20 SES1 kernel: [10396.329067] ata5.00: status: { DRDY }
Jan  2 22:14:20 SES1 kernel: [10396.329087] ata5: soft resetting link
Jan  2 22:14:20 SES1 kernel: [10396.517457] ata5.00: configured for PIO3
Jan  2 22:14:20 SES1 kernel: [10396.533529] ata5.01: configured for UDMA/33
Jan  2 22:14:20 SES1 kernel: [10396.533553] ata5: EH complete
Jan  2 22:14:50 SES1 kernel: [10426.533033] ata5.00: limiting speed to PIO0
Jan  2 22:14:50 SES1 kernel: [10426.533044] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:14:50 SES1 kernel: [10426.533052] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:14:50 SES1 kernel: [10426.533053]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:14:50 SES1 kernel: [10426.533054]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:14:50 SES1 kernel: [10426.533057] ata5.00: status: { DRDY }
Jan  2 22:14:50 SES1 kernel: [10426.533075] ata5: soft resetting link
Jan  2 22:14:51 SES1 kernel: [10426.721602] ata5.00: configured for PIO0
Jan  2 22:14:51 SES1 kernel: [10426.737614] ata5.01: configured for UDMA/33
Jan  2 22:14:51 SES1 kernel: [10426.737627] ata5: EH complete
Jan  2 22:15:21 SES1 kernel: [10456.737033] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:15:21 SES1 kernel: [10456.737048] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:15:21 SES1 kernel: [10456.737053]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:15:21 SES1 kernel: [10456.737060]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:15:21 SES1 kernel: [10456.737069] ata5.00: status: { DRDY }
Jan  2 22:15:21 SES1 kernel: [10456.737089] ata5: soft resetting link
Jan  2 22:15:21 SES1 kernel: [10456.925600] ata5.00: configured for PIO0
Jan  2 22:15:21 SES1 kernel: [10456.941602] ata5.01: configured for UDMA/33
Jan  2 22:15:21 SES1 kernel: [10456.941621] ata5: EH complete
Jan  2 22:15:51 SES1 kernel: [10486.940036] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:15:51 SES1 kernel: [10486.940047] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan  2 22:15:51 SES1 kernel: [10486.940054]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:15:51 SES1 kernel: [10486.940061]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:15:51 SES1 kernel: [10486.940072] ata5.01: status: { DRDY }
Jan  2 22:15:51 SES1 kernel: [10486.940091] ata5: soft resetting link
Jan  2 22:15:51 SES1 kernel: [10487.128616] ata5.00: configured for PIO0
Jan  2 22:15:51 SES1 kernel: [10487.144615] ata5.01: configured for UDMA/33
Jan  2 22:15:51 SES1 kernel: [10487.144634] ata5: EH complete
Jan  2 22:16:21 SES1 kernel: [10517.145034] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:16:21 SES1 kernel: [10517.145050] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:16:21 SES1 kernel: [10517.145056]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:16:21 SES1 kernel: [10517.145063]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:16:21 SES1 kernel: [10517.145073] ata5.00: status: { DRDY }
Jan  2 22:16:21 SES1 kernel: [10517.145093] ata5: soft resetting link
Jan  2 22:16:21 SES1 kernel: [10517.333600] ata5.00: configured for PIO0
Jan  2 22:16:21 SES1 kernel: [10517.349667] ata5.01: configured for UDMA/33
Jan  2 22:16:21 SES1 kernel: [10517.349682] ata5: EH complete
Jan  2 22:16:51 SES1 kernel: [10547.349034] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:16:51 SES1 kernel: [10547.349048] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:16:51 SES1 kernel: [10547.349049]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:16:51 SES1 kernel: [10547.349057]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:16:51 SES1 kernel: [10547.349067] ata5.00: status: { DRDY }
Jan  2 22:16:51 SES1 kernel: [10547.349088] ata5: soft resetting link
Jan  2 22:16:51 SES1 kernel: [10547.537599] ata5.00: configured for PIO0
Jan  2 22:16:51 SES1 kernel: [10547.553598] ata5.01: configured for UDMA/33
Jan  2 22:16:51 SES1 kernel: [10547.553614] ata5: EH complete
Jan  2 22:17:01 SES1 /USR/SBIN/CRON[31104]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  2 22:17:21 SES1 kernel: [10577.553033] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:17:21 SES1 kernel: [10577.553048] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:17:21 SES1 kernel: [10577.553050]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:17:21 SES1 kernel: [10577.553057]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:17:21 SES1 kernel: [10577.553066] ata5.00: status: { DRDY }
Jan  2 22:17:21 SES1 kernel: [10577.553086] ata5: soft resetting link
Jan  2 22:17:22 SES1 kernel: [10577.741602] ata5.00: configured for PIO0
Jan  2 22:17:22 SES1 kernel: [10577.757601] ata5.01: configured for UDMA/33
Jan  2 22:17:22 SES1 kernel: [10577.757615] ata5: EH complete
Jan  2 22:17:52 SES1 kernel: [10607.757038] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:17:52 SES1 kernel: [10607.757052] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:17:52 SES1 kernel: [10607.757058]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:17:52 SES1 kernel: [10607.757066]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:17:52 SES1 kernel: [10607.757078] ata5.00: status: { DRDY }
Jan  2 22:17:52 SES1 kernel: [10607.757099] ata5: soft resetting link
Jan  2 22:17:52 SES1 kernel: [10607.945601] ata5.00: configured for PIO0
Jan  2 22:17:52 SES1 kernel: [10607.961600] ata5.01: configured for UDMA/33
Jan  2 22:17:52 SES1 kernel: [10607.961618] ata5: EH complete
Jan  2 22:18:22 SES1 kernel: [10637.960074] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:18:22 SES1 kernel: [10637.960084] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:18:22 SES1 kernel: [10637.960086]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:18:22 SES1 kernel: [10637.960087]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:18:22 SES1 kernel: [10637.960091] ata5.00: status: { DRDY }
Jan  2 22:18:22 SES1 kernel: [10637.960111] ata5: soft resetting link
Jan  2 22:18:22 SES1 kernel: [10638.157120] ata5.00: configured for PIO0
Jan  2 22:18:22 SES1 kernel: [10638.177120] ata5.01: configured for UDMA/33
Jan  2 22:18:22 SES1 kernel: [10638.177132] ata5: EH complete
Jan  2 22:18:52 SES1 kernel: [10668.180563] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:18:52 SES1 kernel: [10668.180572] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:18:52 SES1 kernel: [10668.180574]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:18:52 SES1 kernel: [10668.180576]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:18:52 SES1 kernel: [10668.180579] ata5.00: status: { DRDY }
Jan  2 22:18:52 SES1 kernel: [10668.180599] ata5: soft resetting link
Jan  2 22:18:52 SES1 kernel: [10668.369120] ata5.00: configured for PIO0
Jan  2 22:18:52 SES1 kernel: [10668.385121] ata5.01: configured for UDMA/33
Jan  2 22:18:52 SES1 kernel: [10668.385129] ata5: EH complete
Jan  2 22:19:22 SES1 kernel: [10698.384553] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  2 22:19:22 SES1 kernel: [10698.384563] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan  2 22:19:22 SES1 kernel: [10698.384564]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan  2 22:19:22 SES1 kernel: [10698.384566]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  2 22:19:22 SES1 kernel: [10698.384570] ata5.00: status: { DRDY }
Jan  2 22:19:22 SES1 kernel: [10698.384590] ata5: soft resetting link
Jan  2 22:19:22 SES1 kernel: [10698.577115] ata5.00: configured for PIO0
Jan  2 22:19:22 SES1 kernel: [10698.601209] ata5.01: configured for UDMA/33
Jan  2 22:19:22 SES1 kernel: [10698.601226] ata5: EH complete
Jan  2 22:32:23 SES1 syslogd 1.5.0#2ubuntu6: restart.
```

why did it freeze? i think it have something to do with the nfs that i always mount. the host is a nslu2 with debian. in my fstab on my desktop i use rw,intr,soft,timeo=15 as options to mount this nfs. if i didn't mount the nfs i usually haven't any freezes. so is there a connection?

pls can you help me?

---

### Post by the-fang on 2009-01-08
can anybody help?

---

