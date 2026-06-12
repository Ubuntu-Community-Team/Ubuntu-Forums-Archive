---
title: "Installing the game farcry"
date: 2005-05-15
forum: Desktop Environments
---

### Post by hellmaker on 2005-05-15
iam a newbie to linux....and have installed ubunt 5.04 for using it to a farcry server.

I got everything up and running, the packages and sarting the server. But when i log on to the game i get this message... does thhis make sence to anybody out there ?

Received signal SIGSEGV: program tries to read or write outside the memory that is allocated for it

Stack-Trace: obtained 10 stack frames.
./farcry_linuxsv [0x804c196]
[0xffffe420]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0xe9) [0xb7f91299]
/home/xxxx/Spill/Far Cry/bin32linux/crygame.so(_ZN12CXServerSlot14OnContextReadyER7CStream+0x2e2) [0xb64a2782]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN15CServerSlotImpl14OnContextReadyEv+0x58) [0xb6f11cd8]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN19CServerStateMachine8OnSignalEjj+0x97) [0xb6f172c7]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN19CServerStateMachine28HandleWAIT_FOR_CONTEXT_READYEjj+0x155) [0xb6f16c15]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN19CServerStateMachine14_ProcessSignalEjm+0x98) [0xb6f16f18]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN13CStateMachine6UpdateEjj+0x92) [0xb6f10662]
/home/xxxx/Spill/Far Cry/bin32linux/crynetwork.so(_ZN15CServerSlotImpl17OnCCPContextReadyER7CStream+0x49) [0xb6f12029]

Avbrutt (SIGABRT)  <--- in norwegian and means: aborted (SIGABRT)

********
Anybody knows what this mean and how to fix it... :???:

---

