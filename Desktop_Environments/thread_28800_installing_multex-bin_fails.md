---
title: "installing multex-bin fails"
date: 2005-04-21
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-04-21
Hi

I've been trying to install multex-bin cause i want a good complete latex package. But there seems to be some trouble in setting it up. I've tried installing it via synaptic, kynaptic or regular apt-get. After the first installation I did a "apt-get install -f" and the following message appears...

sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up multex-bin (0.8.1-7) ...
mktexlsr: Updating /usr/local/share/texmf/ls-R...
mktexlsr: Updating /usr/local/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.
Make format files of multex-bin. This may take some time. ...
  The format file of `multex' is built successfully.
  The format file of `mullatex' is NOT built successfully.
  Visit `/var/lib/texmf/web2c/mullatex.log' for details.
dpkg: error processing multex-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 multex-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm wondering if this is a problem that other persons may have. Try and do an "sudo apt-get install multex-bin" and see if it gives you any trouble. There is no trouble using remove afterwards to get rid of it. But sadly enough I don't know what to do to get it to install correctly.

---

### Post by epb613 on 2005-04-21
I gave it a try; this is what I got.

pinny@pinnys-laptop:~$ sudo apt-get install multex-bin
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  jtex-base libkpathsea3 libt1-5 libwww-ssl0 multex-base tetex-base tetex-bin
  texinfo
Suggested packages:
  gv postscript-viewer xpdf-reader pdf-viewer chktex lacheck rubber
Recommended packages:
  jtex-bin tetex-extra tetex-doc dialog texi2html perl-tk
The following NEW packages will be installed:
  jtex-base libkpathsea3 libt1-5 libwww-ssl0 multex-base multex-bin tetex-base
  tetex-bin texinfo
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.7MB of archives.
After unpacking 71.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main texinfo 4.7-2.2ubuntu1 [474kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main tetex-base 2.0.2c-3 [14.4MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libkpathsea3 2.0.2-25 [57.3kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libt1-5 5.0.2-3 [141kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libwww-ssl0 5.4.0-9 [452kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main tetex-bin 2.0.2-25 [3832kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe jtex-base 1.9.1-3 [112kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe multex-base 0.8-2 [86.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe multex-bin 0.8.1-7 [148kB]
Fetched 19.7MB in 1m53s (173kB/s)

Preconfiguring packages ...
Selecting previously deselected package texinfo.
(Reading database ... 82831 files and directories currently installed.)
Unpacking texinfo (from .../texinfo_4.7-2.2ubuntu1_i386.deb) ...
Selecting previously deselected package tetex-base.
Unpacking tetex-base (from .../tetex-base_2.0.2c-3_all.deb) ...
Selecting previously deselected package libkpathsea3.
Unpacking libkpathsea3 (from .../libkpathsea3_2.0.2-25_i386.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.0.2-3_i386.deb) ...
Selecting previously deselected package libwww-ssl0.
Unpacking libwww-ssl0 (from .../libwww-ssl0_5.4.0-9_i386.deb) ...
Selecting previously deselected package tetex-bin.
Unpacking tetex-bin (from .../tetex-bin_2.0.2-25_i386.deb) ...
Selecting previously deselected package jtex-base.
Unpacking jtex-base (from .../jtex-base_1.9.1-3_all.deb) ...
Selecting previously deselected package multex-base.
Unpacking multex-base (from .../multex-base_0.8-2_all.deb) ...
Selecting previously deselected package multex-bin.
Unpacking multex-bin (from .../multex-bin_0.8.1-7_i386.deb) ...
Setting up texinfo (4.7-2.2ubuntu1) ...

Setting up tetex-base (2.0.2c-3) ...

Creating config file /etc/texmf/mktex.cnf with new version

Creating config file /etc/texmf/dvips/config.builtin35 with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/dvipdfm/config with new version

Creating config file /etc/texdoctk/texdocrc with new version

Setting up libkpathsea3 (2.0.2-25) ...

Setting up libt1-5 (5.0.2-3) ...

Setting up libwww-ssl0 (5.4.0-9) ...

Setting up tetex-bin (2.0.2-25) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version
Generating /etc/texmf/texmf.cnf ...
Creating config file /etc/texmf/texmf.cnf with new version
done
Generating /var/lib/texmf/web2c/fmtutil.cnf ... done
Regenerating /var/lib/texmf/web2c/updmap.cfg ... done
Running initex. This may take some time. ...
fmtutil: /var/lib/texmf/web2c/latex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdftex.fmt installed.
fmtutil: /var/lib/texmf/web2c/tex.fmt installed.
fmtutil: /var/lib/texmf/web2c/cont-en.efmt installed.
fmtutil: /var/lib/texmf/web2c/elatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/etex.efmt installed.
fmtutil: /var/lib/texmf/web2c/latex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mptopdf.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfelatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfetex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mf.base installed.
Running updmap. This may take some time. ...


If you want to change the default settings,
use /usr/bin/texconfig to configure teTeX.

Fixing permissions and group of ls-R as specified by debconf ...
mode of `/var/lib/texmf/ls-R' changed to 0664 (rw-rw-r--)
mode of `/var/lib/texmf/ls-R-TEXMFMAIN' changed to 0664 (rw-rw-r--)
mode of `/var/cache/fonts/ls-R' changed to 0664 (rw-rw-r--)
changed group of `/var/lib/texmf/ls-R' to users
changed group of `/var/lib/texmf/ls-R-TEXMFMAIN' to users
changed group of `/var/cache/fonts/ls-R' to users

Setting up jtex-base (1.9.1-3) ...
mktexlsr: Updating /usr/local/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.

Setting up multex-base (0.8-2) ...
mktexlsr: Updating /usr/local/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.

Setting up multex-bin (0.8.1-7) ...
Replacing config file /etc/texmf/texmf.cnf with new version
mktexlsr: Updating /usr/local/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.
Make format files of multex-bin. This may take some time. ...
  The format file of `multex' is built successfully.
  The format file of `mullatex' is NOT built successfully.
  Visit `/var/lib/texmf/web2c/mullatex.log' for details.
dpkg: error processing multex-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 multex-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
pinny@pinnys-laptop:~$

---

### Post by epb613 on 2005-04-21
And then when I type it in again, I got the exact same results as your inital post.

---

### Post by GoldBuggie on 2005-04-22
Thanks for trying, I appreciate it...that at least makes me think(as i suspected) that it wasn't me. 

So...any expert in the field that knows what the trouble might be? I've been trying to search the net for answers but I haven't found any solution.

---

### Post by mcmv200i on 2006-10-09
I had the same problem: Installing jtex-bin solved the problem for me. I guess this is an unentered dependency.

---

