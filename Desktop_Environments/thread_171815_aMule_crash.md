---
title: "aMule crash"
date: 2006-05-07
forum: Desktop Environments
---

### Post by Disabled on 2006-05-07
Hi, some time ago aMule started crashing after about 20 min i've started it...

I also tried to upgrade to dapper, hoping something would get fixed, but with no use (even if kde 3.5 is very cool :P)

This is the error message taken from the console:
```
Terminated after throwing an instance of 'CEOFException'
        what(): SafeIO::EOF: Attempt to read past end of file.
        backtrace:
[2] ?? in /usr/lib/libstdc++.so.6 [0xb753a915]
[3] ?? in /usr/lib/libstdc++.so.6 [0xb753a94a]
[4] __cxa_rethrow in /usr/lib/libstdc++.so.6[0xb753aad8]
[5] ?? in amule [0x8196ae6]
[6] ?? in amule [0x819704e]
[7] ?? in amule [0x807eab6]
[8] wxThreadInternal::PthreadStart(wxThread*) in /usr/lib/libwx_baseu-2.6.so.0[0xb7629bf0]
[9] wxPthreadStart in /usr/lib/libwx_baseu-2.6.so.0[0xb7629c63]
[10] ?? in /lib/tls/i686/cmov/libpthread.so.0 [0xb7ee4341]
[11] __clone in /lib/tls/i686/cmov/libc.so.6[0xb73ff4ee]

```

Thank you all :P

---

### Post by barbarian on 2006-05-08
Yep, for me the same situation, hopefully it would be fixed in Dapper:sad:

---

