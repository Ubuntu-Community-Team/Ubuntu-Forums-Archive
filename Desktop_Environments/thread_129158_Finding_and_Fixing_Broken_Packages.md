---
title: "Finding and Fixing Broken Packages"
date: 2006-02-13
forum: Desktop Environments
---

### Post by KevNice on 2006-02-13
Hi again,

The package manager icon is lit up, when I click on it, it says I have a broken file. I go into package manager and hit "fix broken dependencies", and it says that there is no longer a broken file. But it still acts broken.

Heres what happens when I use sudo apt-get check:

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  songwrite: Depends: lilypond but it is not installed
E: Unmet dependencies. Try using -f.

so i do -f and I get this:

Unpacking lilypond (from .../lilypond_2.6.3-9~breezy1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

My guess is that this file is defective, but something is broken somewhere and it keeps asking me to download this, but Im not sure what or where. Sorry, this is probably an easy answer, but I am new to Ubuntu (and have no programming experience). Any help is much appreciated.

Thanks

---

### Post by nalmeth on 2006-02-13
Ahh, this seems to have happened to a few people, myself included. Unfortunately I can't remember what I did about it, but here is some reading that might get you somewhere:

[http://ubuntuforums.org/showthread.php?p=680286#post680286](http://ubuntuforums.org/showthread.php?p=680286#post680286)
[http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond](http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond)
[http://www.ubuntuforums.org/showthread.php?p=705969#post705969](http://www.ubuntuforums.org/showthread.php?p=705969#post705969)

From what I can tell, there is something wrong with this package, and it needs the program that depends on it to be installed to work... :-k 
Sorry I can't help you directly, but keep posting your progress.

BTW this is supposed to be all fixed up for the Dapper 6.04 release, I just don't know why they didn't change the .deb for breezy.

EDIT: have you tried ?
sudo apt-get remove songwrite

---

### Post by manicka on 2006-02-13
Open the Synaptic package manager. System --> Administration --> Synaptic Package Manager

If anything is broken it will tell you.
Choose  'Custom' from the buttons at the bottom then  click on 'Broken'

Right click on the offending package and choose to remove it.

---

### Post by KevNice on 2006-02-15
wow, that was easy! Thanks a bunch!

---

### Post by KevNice on 2006-02-17
Now I've got this problem as well. I was able to delete the package that was messing up everything, but the file lilypond-data still won't be deleted. I followed DrakeWolf's instructions, and here's what happened: (warning, very long)

installing tetex-bin:

The following NEW packages will be automatically installed:
libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-doc texi2html
The following NEW packages will be installed:
libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-bin tetex-doc
texi2html
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.3MB of archives. After unpacking 116MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe lilypond-data 2.6.3-9~breezy1 [4736kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libwww-ssl0 5.4.0-9ubuntu0.5.10 [448kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main tetex-bin 2.0.2-30ubuntu3.4 [3884kB]
Get:4 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main tetex-base 2.0.2c-8 [14.4MB]
Get:5 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main libt1-5 5.0.2-3 [141kB]
Get:6 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main tetex-doc 2.0.2c-8 [28.2MB]
Get:7 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe perl-tk 1:800.025-2 [2380kB]
Get:8 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main psutils 1.17-17 [81.3kB]
Get:9 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main texi2html 1.66-1.2 [93.8kB]
Fetched 54.3MB in 9m8s (99.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 69025 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
subprocess post-removal script returned error exit status 1
Selecting previously deselected package tetex-base.
Unpacking tetex-base (from .../tetex-base_2.0.2c-8_all.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.0.2-3_i386.deb) ...
Selecting previously deselected package libwww-ssl0.
Unpacking libwww-ssl0 (from .../libwww-ssl0_5.4.0-9ubuntu0.5.10_i386.deb) ...
Selecting previously deselected package tetex-bin.
Unpacking tetex-bin (from .../tetex-bin_2.0.2-30ubuntu3.4_i386.deb) ...
Selecting previously deselected package tetex-doc.
Unpacking tetex-doc (from .../tetex-doc_2.0.2c-8_all.deb) ...
Selecting previously deselected package perl-tk.
Unpacking perl-tk (from .../perl-tk_1%3a800.025-2_i386.deb) ...
Selecting previously deselected package psutils.
Unpacking psutils (from .../psutils_1.17-17_i386.deb) ...
Selecting previously deselected package texi2html.
Unpacking texi2html (from .../texi2html_1.66-1.2_all.deb) ...
Errors were encountered while processing:
/var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack! Something bad happened while installing packages. Trying to recover:
Setting up libt1-5 (5.0.2-3) ...

Setting up texi2html (1.66-1.2) ...
Setting up tetex-base (2.0.2c- ...

Creating config file /etc/texmf/mktex.cnf with new version

Creating config file /etc/texmf/dvips/config.builtin35 with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/dvipdfm/config with new version

Creating config file /etc/texdoctk/texdocrc with new version

Setting up libwww-ssl0 (5.4.0-9ubuntu0.5.10) ...

Setting up perl-tk (800.025-2) ...
Setting up tetex-bin (2.0.2-30ubuntu3.4) ...

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

Setting up psutils (1.17-17) ...

Setting up tetex-doc (2.0.2c- ...
mktexlsr: Updating /usr/local/share/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done



depackaging:

sudo dpkg -i /var/cache/apt/archives/tetex-bin_2.0.2-30ubuntu3.4_i386.deb
(Reading database ... 79238 files and directories currently installed.)
Preparing to replace tetex-bin 2.0.2-30ubuntu3.4 (using .../tetex-bin_2.0.2-30ubuntu3.4_i386.deb) ...
Unpacking replacement tetex-bin ...
Setting up tetex-bin (2.0.2-30ubuntu3.4) ...
Merging information from /etc/texmf/texmf.d/ into /etc/texmf/texmf.cnf ... done
Regenerating /var/lib/texmf/web2c/fmtutil.cnf ... done
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


removing:

sudo aptitude remove tetex-bin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-doc texi2html
The following packages will be REMOVED:
tetex-bin
0 packages upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B/4736kB of archives. After unpacking 116MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

Preconfiguring packages ...
(Reading database ... 79238 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
(Reading database ... 80182 files and directories currently installed.)
Removing tetex-bin ...
Removing libt1-5 ...
Removing libwww-ssl0 ...
Removing perl-tk ...
Removing psutils ...
Removing tetex-base ...
Removing tetex-doc ...
Removing texi2html ...
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack! Something bad happened while installing packages. Trying to recover:
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
lilypond-data
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done



I have no idea what's going on here. Please help!! 

The lilypond-data file keeps screwing up and messing with stuff whenever I try to download or install anything. I dont know what to do..

---

