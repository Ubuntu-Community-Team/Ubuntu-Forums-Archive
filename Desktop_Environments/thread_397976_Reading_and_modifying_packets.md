---
title: "Reading and modifying packets"
date: 2007-03-31
forum: Desktop Environments
---

### Post by DeathOnJuice on 2007-03-31
Hey, everybody. I've been looking around for some ways to read and modify incoming and outgoing packets (of my local computer, not the whole network), but I have yet to find a secure solution. I have already, of course, heard of tools such as Wireshark and TCPDump, but these are not very secure as far as I understand. Also, I don't think they can modify packets, but I may be wrong. If I can only read, that would be fine for my current purposes, but I always like to explore. Anyway I only need to make this work for my local computer, so is there a way to configure them to not listen to traffic from others on the network? Would this be secure? If not, is there a better tool for my purposes?

Thanks in advance!

---

### Post by yabbadabbadont on 2007-03-31
I'm curious.  What valid reason (i.e. not crackerish in nature) do you have to want to do this?

---

### Post by DeathOnJuice on 2007-03-31
I figured I would get a response like this. However, if you think, there's really nothing crackerish about this. I'm only doing it on my local computer, so I can't really tamper with the connections of other computers on the network (which would be easy enough with Ettercap or something of the like). The only other "crackerish" thing I can think of doing is hacking the high score boards of little flash games, which I am well above and could do much more easily with Tamper Data, a Firefox extension which my friend does use for this.

Besides, you can't really do anything modifying small, individual packets.

I am mainly doing this for curiosity. I love to look at how things work hands-on; recently I have compiled kernels for the first time, taken apart old PCI cards, read system files, and other things of the like. Today's project is looking into packets a bit.

---

### Post by DeathOnJuice on 2007-04-01
No one? Is this because nobody knows, or do you just not trust me? Fine. Can anyone think of any malicious thing that I haven't already covered that can be done with this? Please be reasonable.

---

### Post by yabbadabbadont on 2007-04-01
Read the RFC's for the TCP/IP suite of protocols.  That will explain exactly how the packets are formed and what each part does.  It also explains the flow of packets and proper request/response in all situations.  Once you understand that, you will have the knowledge needed to do what you are asking about.

---

### Post by DeathOnJuice on 2007-04-01
Thanks! I'll check it out.

---

