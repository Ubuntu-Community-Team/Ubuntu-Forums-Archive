---
title: "Citrix NFUSE Certificate problem"
date: 2006-03-30
forum: Desktop Environments
---

### Post by dpack on 2006-03-30
I have downloaded and installed the Citrix ICA client from Citrix's web site. Firefox shows the ICA plugin. I log into my company's NFUSE site successfully. I then click on one of our published applications and Citrix starts to run and then I get this message: “You have not chosen to trust "Thawte Server CA", the issuer of the server's security certificate."

I went to [http://www.thawte.com/roots/](http://www.thawte.com/roots/) and downloaded the zip file. I copied the ThawteServerCA.txt, ThawteServerCA.509, and ThawteServerCA.cer to the /usr/lib/ICAClient/keystore/cacerts directory. I copied the the three files just as they are into the directory without renaming anything. I went into the Manage Certificates in FireFox and it shows the Thawte Server CA certificate is installed. I still get the above error message. Any thoughts?

](*,)  I'm so close to getting it! lol

---

### Post by clayton on 2006-03-31
No help here, but I am experiencing the same problem, only with an Equifax certificate. Firefox acknowledges the certificate, I get past the first screen, but after clicking on an application icon, I get the "You have not chosen to trust ... Equifax Secure Certificate Authority..." with only a Quit button.

---

### Post by clayton on 2006-03-31
I fixed my setup by putting the cert in /usr/lib/Icaclient/keystore/cacerts. All of the files in that directory have .crt extensions, as the one I downloaded did. Perhaps rename your cert?

---

### Post by dpack on 2006-03-31
Renaming the ThawteServerCA.cer to ThawteServerCA.crt worked. Thanks!

---

### Post by ironopolis on 2006-12-13
> **clayton said:**
> I fixed my setup by putting the cert in /usr/lib/Icaclient/keystore/cacerts. All of the files in that directory have .crt extensions, as the one I downloaded did. Perhaps rename your cert?


hi clayton

which cert are you talking about??? having the same problem as you.

thanks for any help

ironpolis

---

### Post by filippod on 2007-01-05
> ***ironopolis** wrote: *
hi clayton, which cert are you talking about??? having the same problem as you.

If (like Clayton was) you're missing an Equifax certificate you can find it here: [http://www.geotrust.com/resources/root_certificates/index.asp](http://www.geotrust.com/resources/root_certificates/index.asp)

If you need another certificate you should be able to find it on the respective Certificate Authority website. A Google search should help.

Once you've obtained the correct certificate you have to copy it to /usr/lib/ICAClient/keystore/cacerts and change the extension from .cer (or whatever it is) to .crt

You can also find a full discussion of the subject on this thread: [http://ubuntuforums.org/showthread.php?t=85398&page=3](http://ubuntuforums.org/showthread.php?t=85398&page=3)

---

