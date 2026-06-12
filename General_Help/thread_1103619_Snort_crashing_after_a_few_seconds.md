---
title: "Snort crashing after a few seconds"
date: 2009-03-22
forum: General Help
---

### Post by john.belcher on 2009-03-22
Not sure if this is a question for "General"

I have had snort+mysql+base running for a few weeks.  After doing among other things a dist upgrade to 8.10, I noticed that snort was no longer running.  The snort daemon starts and runs for a few seconds than stops.

This is what I get in /var/log/messages

```
Mar 22 19:46:33 box kernel: [23836.482468] device eth0 entered promiscuous mode
Mar 22 19:46:48 box kernel: [23852.227597] snort[7929]: segfault at 18 ip b79ee323 sp bfd975d0 error 4 in libc-2.8.90.so[b7977000+158000]
Mar 22 19:46:48 box kernel: [23852.231070] device eth0 left promiscuous mode
```

This is what i get from starting snort manually sudo snort -c /etc/snort/snort.conf


```
        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.7.0 (Build 35)
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.6  <Build 11>
           Preprocessor Object: SF_SMTP  Version 1.0  <Build 7>
           Preprocessor Object: SF_SSH  Version 1.0  <Build 1>
           Preprocessor Object: SF_FTPTELNET  Version 1.0  <Build 10>
           Preprocessor Object: SF_DCERPC  Version 1.0  <Build 4>
           Preprocessor Object: SF_DNS  Version 1.0  <Build 2>
Not Using PCAP_FRAMES
Segmentation fault
```

Can someone point me in the right direction?

Thanks in advance.

---

