---
title: "How do i compile nmap 4.85BETA7 on intrepid? I am getting errors"
date: 2009-04-02
forum: General Help
---

### Post by sefs on 2009-04-02
How do i compile nmap 4.85BETA7 on intrepid? I am getting errors.

The first error occurs after running make the first time is:
```

Makefile:302: makefile.dep: No such file or directory
g++ -MM -Iliblua -Ilibdnet-stripped/include -Ilibpcre  -Ilibpcap -Inbase -Insock/include main.cc nmap.cc targets.cc tcpip.cc nmap_error.cc utils.cc idle_scan.cc osscan.cc osscan2.cc output.cc scan_engine.cc timing.cc charpool.cc services.cc protocols.cc nmap_rpc.cc portlist.cc NmapOps.cc TargetGroup.cc Target.cc FingerPrintResults.cc service_scan.cc NmapOutputTable.cc MACLookup.cc nmap_tty.cc nmap_dns.cc traceroute.cc portreasons.cc nse_main.cc nse_nsock.cc nse_init.cc nse_fs.cc nse_nmaplib.cc nse_debug.cc nse_pcrelib.cc nse_binlib.cc nse_bit.cc nse_openssl.cc  > makefile.dep
/bin/sh: g++: not found
make: *** [makefile.dep] Error 127

```

I immediately run make again and it begins to go thru a lot of lines that end with:

```

make[1]: g++: Command not found
make[1]: *** [main.o] Error 127
make[1]: Leaving directory `/home/lalaland/Desktop/nmap-4.85BETA7'
make: *** [all] Error 2

```

Any idea how to get this thing compiled? I want to do some confiker probing.

---

### Post by kanikilu on 2009-04-02
It doesn't look like you have a compiler installed. I believe the 'build-essential' package will install the things you need: ```
sudo apt-get install build-essential
```

Also, it's of course up to you, but I skipped the last step (**make install**) when compiling, because I wanted to keep it separate from the packaged nmap that I installed earlier. It just leaves the new binary in the directory where you compiled it, and it can be run from there with ```
./nmap <options>
```

---

### Post by sefs on 2009-04-02
Thank you...i wonder why i don't have that installed.  It is usually one of the first things I do.  Must be conifiker must have done it.

---

### Post by sefs on 2009-04-02
I note that the new zenmap comes with this as well.  What I would like to do is remove the ones from the repos...and make install this one....but...if i dont like it is there an easy way to remove it cleanly?

Edit:  It probably would decompress the archive run ./config, run make, then run sudo make uninstall?

---

