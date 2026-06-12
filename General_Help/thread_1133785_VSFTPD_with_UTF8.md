---
title: "VSFTPD with UTF8"
date: 2009-04-23
forum: General Help
---

### Post by sistematico on 2009-04-23
I use vsftpd and many people are accessing my FTP they have problems with accents and cedilla.
The vsftpd is in UTF-8 and folders it too, when Firefox is in UTF-8 everything is normal.

However, I do not know why Firefox recognizes my FTP as ISO-8859-1 and then the folders with accents or cedilla are mangled and impossible to access.

I have a way of "forcing" the Firefox to read in UTF-8 without the user change the settings of the Browser?
Is there any other way?

Thank you and sorry for bad english..

-------------- OLD POST -------------------
I'm having a problem with vsftpd he does not read directories that have accents, my locale is set to pt_BR.UTF8, anyone know how to resolve this?

I found a patch for this in [http://vsftpd.devnet.ru](http://vsftpd.devnet.ru) but I can not apply a patch.

Ex.: Engraçadas -> EngraÃ§adas
------------------------------------------

---

