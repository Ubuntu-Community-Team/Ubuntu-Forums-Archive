---
title: "Clean print heads problems"
date: 2009-09-22
forum: Desktop Environments
---

### Post by dargaud on 2009-09-22
Hello all,
I have this problem on 2 different computers with jaunty x86-64 and CUPS. One with an Epson R1800 printer (Foomatic/gutemprint-ijs) the other with a Canon i560 (i560-CUPS-Gutemprint). They both print properly, but if I try to do a self test or a head cleaning, I get an error "*There was an error during the CUPS operation: 'client-error-document-format-not-supported'*".

There are many hits when I search for this on google, but none have solved the problem (I've added RAW to the mime.convs / mime.types files).

Anything else ?

---

### Post by clonne4crw on 2009-09-27
You might want to have a look at these and make sure you have the right drivers installed, even though you seem to with the Epson one:

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R1800](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R1800)

[http://openprinting.org/show_printer.cgi?recnum=Canon-i560](http://openprinting.org/show_printer.cgi?recnum=Canon-i560)

Notice how the Canon is give only partial support.

---

### Post by dargaud on 2009-09-30
The drivers I have are:
```
Epson Stylus Photo R1800 Foomatic/gutenprint-ijs-simplified.5.2
Canon i560 - CUPS+Gutenprint v5.2.3 Simplified
```I don't how how those match the drivers on the page you point to, in particular  x86 64 bit (DEB for LSB 3.1) vs x86 64 bit (DEB for LSB 3.2).

The important thing is that the Canon prints too yellow, which is to me a symptom of an uncalibrated driver or not enough blue, either from an empty tank or a stuck head. But how do you diagnose that if you can't print a self-test page ?

---

