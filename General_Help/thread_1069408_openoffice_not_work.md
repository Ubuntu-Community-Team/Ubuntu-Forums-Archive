---
title: "openoffice not work"
date: 2009-02-13
forum: General Help
---

### Post by parsibox on 2009-02-13
hi
i update my openoffice but now it dose not work
```

opemohsen@mohsen-laptop:~$ openoffice
/usr/lib/openoffice/program/soffice: 214: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 231: /usr/lib/openoffice/program/soffice.bin: not found
mohsen@mohsen-laptop:~$ 

```

how can i fix it?
open office also is not  in my menu list now( but older it was in my menu )
i use ubuntu 8.4

---

### Post by fragos on 2009-02-14
Your problem may be in how you updated your OpenOffice. Probably you were updating to OO 3. Packages should always come from mrepositories specifically built for your version of Ubuntu. Open up System-> Administration-> Software Sources-> Third-Party tab-> Add... button.

URI: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/)
Distrobution: hardy
Components: main

Close button and OO 3 will be available to install and the Update Manager should offer it the next time it runs, usually once a day.

---

