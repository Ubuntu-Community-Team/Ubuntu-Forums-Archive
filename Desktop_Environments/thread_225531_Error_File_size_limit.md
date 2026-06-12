---
title: "Error: File size limit"
date: 2006-07-29
forum: Desktop Environments
---

### Post by waffen on 2006-07-29
Hello,

When I try to download this file via Firefox 1.5.0.5:
[http://linorg.usp.br/OpenOffice.org/stable/1.1.0_sdk/OOo_1.1.0_LinuxIntel_sdk.tar.gz]("http://linorg.usp.br/OpenOffice.org/stable/1.1.0_sdk/OOo_1.1.0_LinuxIntel_sdk.tar.gz")

I receipt this error:
```

Attention!!!

The file "OOo_1.1.0_LinuxIntel_sdk.tar.gz" has been blocked. The file is larger than the configured file size limit.

URL = http://linorg.usp.br/OpenOffice.org/stable/1.1.0_sdk/OOo_1.1.0_LinuxIntel_sdk.tar.gz
```

And when I try to use wget:

```
mario@laptop:~$ wget http://api.openoffice.org/docs/DevelopersGuide/DevelopersGuide.pdf
--19:57:31--  http://api.openoffice.org/docs/DevelopersGuide/DevelopersGuide.pdf
           => `DevelopersGuide.pdf'
Resolviendo api.openoffice.org... 204.16.104.2
Conectando a api.openoffice.org|204.16.104.2|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 Ok
Longitud: no especificado [text/html]

    [ <=>                                                                                                                        ] 244           --.--K/s

19:57:33(7.51 MB/s) - `DevelopersGuide.pdf' guardado [244]

```

In both case, I only download a file with 244 KB and the original file size is: 25MB

Before I just update my Firefox from 1.5.0.4 the download option work fine, any idea??

Thanks ins advance!

---

### Post by fragos on 2006-07-29
I would doubt the problem is on your end.  I do many large downloads with Firefox and have never had a problem like that.  Perhaps the file is corrupted.

---

### Post by waffen on 2006-07-29
Not, because I test trying to download the Xubuntu ISO Image (+600MB) and receipt the same response.

And before the perform the upgrade I download big files with no problem.

---

### Post by waffen on 2006-09-23
Solution: My ISP restric the size for downloads without advise.

Thanks!

---

