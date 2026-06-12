---
title: "PNI / SSE3 Encoding Issue"
date: 2009-05-29
forum: General Help
---

### Post by nickscash on 2009-05-29
First time poster, long time searcher...

I'll try to keep this short and simple.

-I'm encoding videos into x264 with Handbrake and have been trying to have it recognize that my CPU has SSE3. x264 states that my cpu has MMX and SSE2Slow.

-I've compiled both programs from source using various CFLAGS (such as march-k8-sse3, -msse3, etc...), but it won't change anything. My /proc/cpuinfo/ states that I have "PNI" not "SSE3".

-My current system is Ubuntu 9.04 x64 running on a Turion 64 X2, TL-60.

If anyone can help me figure out how to get x264 to see my proper CPU Flags, that would be great.

Thanks,
-Nic

---

