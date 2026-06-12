---
title: "Perl error, please help !"
date: 2006-08-27
forum: Desktop Environments
---

### Post by denday on 2006-08-27
I was run perl script, but i became error :
```
Can't locate String/CRC32.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./search.pl line 30.
BEGIN failed--compilation aborted at ./ffsearch.pl line 30.

```

What this mean & how to fix it ? 

thanks. :grin:

---

### Post by peabody on 2006-08-27
The script apparently needs a perl module you don't have installed:

sudo apt-get install libstring-crc32-perl

---

### Post by denday on 2006-08-27
thanks, It works :cool: :cool:

---

