---
title: "Ubuntu compatable D630 wireless cards?"
date: 2012-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Prometheus418 on 2012-07-03
Hello-

I have a Dell Latitude D630 with the broadcomm wireless card running Ubuntu 12.04.

I have gotten the wifi to work *most* of the time, but it gets spotty now and then, and I am just getting tired of constantly troubleshooting it.  My understanding is that this card has poor linux support because of the manufacturer, and a quick search indicated that a new wireless card is pretty cheap.

So, what I am looking for is an N-band wireless card (may as well upgrade while I'm at it) that will fit a Dell D630, and has better Linux drivers than the one that came in the machine.  If anyone has any suggestions, I would appreciate it.  While I'm capable of shopping for hardware, it's not always clear what the differences between Linux and Windows are (for example, supporting 8gb of RAM in 32-bit Linux, where 3.25gb is the limit in 32-bit Windows systems.)

The spec sheet for this machine offers the following options:
Dell Wireless 1390 (802.11g); Dell Wireless 1490 (802.11a/g); Dell Wireless 1505 (802.11a/g/Draft n); Intel PRO/Wireless 3945AG (802.11a/g); 
Intel PRO/Wireless 4965AGN (802.11a/g/ Draft n)

Edit:

Decided to go with the Intel Wireless WiFi Link 4965AGN, because they provided Linux drivers on their site.  For $12, it seemed like a reasonable level of risk to try it out.

---

### Post by kurt18947 on 2012-07-03
For an Intel 4965AGN, you shouldn't have to anything except install and start Ubuntu.  I have that card in a Thinkpad X61 and it's perfect.  You might have to redo network connections though.  I find with USB adapters that if I switch from a RealTek 8192SU to an Atheros 9xxx, my network connection is sometimes not recognized.  I delete the wireless connection, recreate it with the new card plugged in and I'm back in business.  I've never had the .........'pleasure' ........ of dealing with Broadcom WiFi so don't know if your current firmware/software will persist and cause you grief.

---

### Post by Zaxy13 on 2012-07-05
I have a Dell D630 as well and was wondering if it worked? it would be nice to upgrade.

---

### Post by Prometheus418 on 2012-07-05
Yes-

I got it in the mail today, and made the switch.  The only little snag was about a minute long- when I removed the keyboard and saw that the Broadcom card only had two antennae.  But the third wire was in the machine, tucked into a channel and capped off with a plastic sleeve.

A quick search indicated that the white wire goes to "1", gray="2" and black="3".  They're kind of tricky to clip on, but when I rebooted, the system found it, dumped the broadcom drivers and installed the correct one without any input from me.

I am not getting N-band speed on the 2.4GHz channel, but I do get something very near it on the 5GHz channel.  At first I was annoyed by that, but then I realized that 54mbps is slightly faster than my internet connection anyway, so unless I'm transferring files, it really doesn't matter.  I'll just switch to the 5GHz channel if needed (2.4GHz has better signal strength, so I'm leaving that as the default.)

The important thing is- no dropped connections yet, and that makes it $12 well spent.  I did try to make it drop intentionally by moving some big files around the network (which was what was killing the connection before) and there were no issues.

---

