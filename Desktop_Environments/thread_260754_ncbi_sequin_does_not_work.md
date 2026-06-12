---
title: "ncbi sequin does not work"
date: 2006-09-19
forum: Desktop Environments
---

### Post by tristan@Ubuntu on 2006-09-19
Hello,

With the package ncbi-tools-x11, is coming the sequin program (used to prepare DNA sequence submission to NCBI). On Dapper (32 or 64bit) it does not work:
```

[tristan@babylon ~] sequin
Couldn't find X visual appropriate for OpenGL!
```

If I try to use the binary from NCBI:
```
[tristan@babylon sequin] ./sequin
./sequin: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory
```

but:
```
[tristan@babylon sequin] locate libXm.so.2
/usr/lib/libXm.so.2.0.1
/usr/lib/libXm.so.2
```

Any idea?
Do you know where I should report that bug?

Thanks, 
Tristan

---

### Post by tristan@Ubuntu on 2006-09-20
bug reported in launchpad: #61504
Tristan

---

