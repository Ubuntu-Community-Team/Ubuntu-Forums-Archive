---
title: "Synaptic broken archive"
date: 2006-09-20
forum: Desktop Environments
---

### Post by linuxican on 2006-09-20
Hi,
I'm having a problem with my synaptic in dapper. the problem appeared after i tried to install a wrong package to make my internal modem work. it was a conexant package. it didn't get installed though because of dependencies.
After whenever i try to open synaptic, at first it tells me about a broken package:

> Warning:
You have 1 broken package on your system!
Use the "Broken" filter to locate it.
and then it shows this error message:

> E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

after that synaptic has no packages listed, nothing.
when i try to fix the broken package ( Edit -> Fix broken packages) it says:
> E: I wasn't able to locate file for the conexant package. This might mean you need to manually fix this package.

how should i fix it manually? i even tried to remove it but apt-get remove doesn't work.
Thanks,

---

### Post by kick6 on 2006-09-20
have you tried a ```
dpkg -a
```?

I think that is the command that apt-get suggests whenever it blows up.

---

### Post by linuxican on 2006-09-21
That doesn't work:(
somebody help with this, it's frustrating.

---

