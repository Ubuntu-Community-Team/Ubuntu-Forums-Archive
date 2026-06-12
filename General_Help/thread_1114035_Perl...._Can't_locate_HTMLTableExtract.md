---
title: "Perl.... Can't locate HTML::TableExtract"
date: 2009-04-02
forum: General Help
---

### Post by 24*7 on 2009-04-02
How should the following error be resolved??? 


```
Can't locate **HTML/TableExtract.pm **in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at Extractinfo.pl line 8.
BEGIN failed--compilation aborted at Extractinfo.pl line 8.

```

Even installation of .tar.gz from [http://www.cpan.org/modules/01modules.index.html](http://www.cpan.org/modules/01modules.index.html) by following the instructions given in [http://www.cpan.org/modules/INSTALL.html](http://www.cpan.org/modules/INSTALL.html) is of no use!!

Similar problems is also occuring with **XMLWriter **module of CPAN!!!


How should these issues be resolved?

---

### Post by aduxas on 2010-09-11
This is an old post, but since others may stumble upon it, the solution I found is this:

I found the missing piece by running:

sudo apt-cache search TableExtract

This says:

libhtml-tableextract-perl - module for extracting the content contained in tables within an HTML document

Finally:

sudo apt-get install libhtml-tableextract-perl

---

