---
title: "tar.gz files"
date: 2009-06-02
forum: General Help
---

### Post by smartdude4ever on 2009-06-02
Hi everyone!
I just recently downloaded the driver for my printer (canon lbp 1210)
Its a tar.gz file
I don't know what type of file this is........so please help me.....i want to install my printer driver
the new deb packages are a better way.......but it is only available in tar.gz. So how do i install it?

---

### Post by dandnsmith on 2009-06-02
Start by reading the Man pages for *tar*.

The file extensions show that it is a gzipped tar file - which tar can unpack in one go (but you can do it as a 2 stage if you do *gzip -u* first).

Once unpacked, look for a README or other info file to see what is says to do next.

---

### Post by coffeecat on 2009-06-02
Did you get your tar.gz file from the same download page as is linked under 'Recommended driver' on this page?

[http://openprinting.org/show_printer.cgi?recnum=Canon-LBP-1210](http://openprinting.org/show_printer.cgi?recnum=Canon-LBP-1210)

If so, it says that the tar.gz file contains a number of packages for different distros. To untar the tar.gz file, simply double-click on it and choose extract. The package inside that you want is the .deb file. To install this, simply double-click on that as well.

But as **dandnsmith** said, check for a README first and read that.

---

