---
title: "Mutt-patched"
date: 2009-05-26
forum: General Help
---

### Post by ooolongT on 2009-05-26
So I just started using Mutt to send emails and I love it!  I am wondering if anyone has any experience with the sidebar patch for it. 

I installed the mutt-patched - 1.5.18-6ubuntu1 package from the repos and have made the changes to my muttrc as prescribed by [http://www.lunar-linux.org/index.php?page=mutt-sidebar](http://www.lunar-linux.org/index.php?page=mutt-sidebar) and everything is working fine except that sidebar.  When I hit "b" I get booted out of mutt and this is what I see:

```

b79c0000-b79c1000 r--p 00006000 08:11 465391     /lib/tls/i686/cmov/libnss_compat-2.9.so
                           b79c1000-b79c2000 rw-p 00007000 08:11 465391     /lib/tls/i686/cmov/libnss_compat-2.9.so
                        b79d0000-b79d1000 r-xp 00000000 08:11 407387     /usr/lib/gconv/ISO8859-1.so
         b79d1000-b79d2000 r--p 00001000 08:11 407387     /usr/lib/gconv/ISO8859-1.so
                                                                                     b79d2000-b79d3000 rw-p 00002000 08:11 407387     /usr/lib/gconv/ISO8859-1.so
                                                                      b79d3000-b79d4000 rw-p b79d3000 00:00 0
                   b79d4000-b7a13000 r--p 00000000 08:11 896886     /usr/lib/locale/en_US.utf8/LC_CTYPE
            b7a13000-b7afe000 r--p 00000000 08:11 896885     /usr/lib/locale/en_US.utf8/LC_COLLATE
       b7afe000-b7b00000 rw-p b7afe000 00:00 0
                                               b7b00000-b7b03000 r-xp 00000000 08:11 447989     /lib/libgpg-error.so.0.3.0
                               b7b03000-b7b04000 rw-p 00002000 08:11 447989     /lib/libgpg-error.so.0.3.0
               b7b04000-b7b05000 rw-p b7b04000 00:00 0
                                                       b7b05000-b7b6b000 r-xp 00000000 08:11 447987     /lib/libgcrypt.so.11.4.4
                                     b7b6b000-b7b6c000 r--p 00065000 08:11 447987     /lib/libgcrypt.so.11.4.4
                   b7b6c000-b7b6e000 rw-p 00066000 08:11 447987     /lib/libgcrypt.so.11.4.4
 b7b6e000-b7b82000 r-xp 00000000 08:11 448081     /lib/libz.so.1.2.3.3
                                                                      b7b82000-b7b83000 r--p 00013000 08:11 448081     /lib/libz.so.1.2.3.3
                                                b7b83000-b7b84000 rw-p 00014000 08:11 448081     /lib/libz.so.1.2.3.3
                          b7b84000-b7b94000 r-xp 00000000 08:11 865776     /usr/lib/libtasn1.so.3.0.16
           b7b94000-b7b95000 r--p 0000f000 08:11 865776     /usr/lib/libtasn1.so.3.0.16
                                                                                       b7b95000-b7b96000 rw-p 00010000 08:11 865776     /usr/lib/libtasn1.so.3.0.16
                                                                        b7b96000-b7bab000 r-xp 00000000 08:11 465404     /lib/tls/i686/cmov/libpthread-2.9.so
                                                                  b7bab000-b7bac000 r--p 00014000 08:11 465404     /lib/tls/i686/cmov/libpthread-2.9.so
                                                            b7bac000-b7bad000 rw-p 00015000 08:11 465404     /lib/tls/i686/cmov/libpthread-2.9.so
                                                      b7bad000-b7baf000 rw-p b7bad000 00:00 0
   b7baf000-b7bc1000 r-xp 00000000 08:11 465406     /lib/tls/i686/cmov/libresolv-2.9.so
                                                                                       b7bc1000-b7bc2000 r--p 00011000 08:11 465406     /lib/tls/i686/cmov/libresolv-2.9.so
                                                                                b7bc2000-b7bc3000 rw-p 00012000 08:11 465406     /lib/tls/i686/cmov/libresolv-2.9.so
                                                                         b7bc3000-b7bc6000rw-p b7bc3000 00:00 0
                      b7bc6000-b7bc8000 r-xp 00000000 08:11 447994     /lib/libkeyutils-1.2.so
   b7bc80Aborted
```
Sorry that is so ugly, it is a copy and paste

Unfortunately, I have no idea what that means.  Can anyone give me some help or insight?

Thanks!

---

