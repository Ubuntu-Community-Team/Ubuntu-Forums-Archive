---
title: "problem with printing."
date: 2013-01-07
forum: Desktop Environments
---

### Post by DimiOrla on 2013-01-07
Hei Everyone,
I have a problem with printing.
I use the [KEscPos printer driver for PHP]("http://www.terrasco.net/d-files.php?a=Software:PHP_Libraries&s=pub&f=KEscPos_v1-1.tar&l=both") (you can use the printer with its printer name or port).
On Ubuntu 12.4 everything works but on lubuntu 12.4 
I can only use the printer directly by its port (their for losing the cups printer spool).
I thing it has something to do with the LXDE enviroment, But I wouldent know whare to start looking (beginner linux user)
Theanks in advance for any help.
P.S.
Same Hardware, PHP version and cups printer settings (generic text only)

---

### Post by sudodus on 2013-01-07
Is it on the same or on different computers?

One way might be to install [vanilla] Ubuntu (even if it is slow), and install the printer into it. Then you can install lubuntu-desktop

```
sudo apt-get install lubuntu-desktop
``` and select desktop environment at the login screen, so that you can get the ultra-light Lubuntu flavour.

---

### Post by DimiOrla on 2013-01-07
I have tried lubuntu and ubuntu on an other pc to exclude hardware but
printing by printer name would not work in lubuntu.
On the pc in question the ubuntu installation does not support the processor(dont remember the error) 
I have tried older versions of ubuntu with no results (so a LXDE installation on top is not possible).
The lubuntu installation has no problem with the processor!
Thank you for your help.

---

### Post by sudodus on 2013-01-07
I see that you have tried that already. Is the problem, that your cpu does not have pae?

In that case there is also Xubuntu, between Lubuntu and Ubuntu concerning how much horsepower it needs. Xubuntu has more tools than Lubuntu, and I think Xubuntu 12.04 LTS has a 32-bit non-pae kernel.

So you may have a chance to succeed with Xubuntu 12.04.

Edit: What about your printer driver? Is it something you downloaded? 32-bit or 64-bit? Could you get a suitable version for Lubuntu or Xubuntu?

---

### Post by DimiOrla on 2013-01-07
I will try xubuntu. Although I thing that the problem has to do with file/user permitions (but I dont know how to further investigate)
The printer "driver" is a PHP script talking to the printer port or printer name(given in cups as a standard generic text only printer).
Thanks again.

---

