---
title: "downloading  Quantian now"
date: 2006-09-23
forum: Debian
---

### Post by RAV TUX on 2006-09-23
[http://dirk.eddelbuettel.com/quantian.html](http://dirk.eddelbuettel.com/quantian.html)

just wondering if anybody is currently using Quantian?

            [IMG]http://dirk.eddelbuettel.com/images/trans.gif[/IMG]
> **The *Quantian Scientific Computing Environment***

  A Knoppix / Debian variant tailored to numerical and quantitative analysis. 
 **Executive Summary:** * The most recent version is **0.7.9.2 dated 26 February 2006 and released March 1, 2006 ** --- the second Quantian version based on the new Knoppix 4.0.2 release. The (compressed) iso file is now 2.7 gb and corresponds to about 7.6 gb of software -- all configured and ready to be booted and used. *
 *Support for openMosix has been backported from clusterKnoppix v3.6 with the reliable openMosix-enabled 2.4.27 kernel. The [packages list ordered by size]("http://dirk.eddelbuettel.com/quantian/quantian_0.7.9.2.quantian.txt") and the [detailed packages list]("http://dirk.eddelbuettel.com/quantian/quantian_0.7.9.2.quantian.packages.txt") provide details about the included programs, see the [changelog]("http://dirk.eddelbuettel.com/quantian/changelog.html") for a detailed summary of all the changes. Download informations are provided below. Also see the [Quantian blog page]("http://dirk.eddelbuettel.com/blog/computers/linux/debian/quantix/index.html"), the [changelog]("http://dirk.eddelbuettel.com/quantian/changelog.html"), the [todo]("http://dirk.eddelbuettel.com/quantian/todo.html") and [bugs]("http://dirk.eddelbuettel.com/quantian/bugs.html") pages, and well as the set of short [howtos ]("http://dirk.eddelbuettel.com/quantian/howto.html") for detailed information.* 
**What is Quantian?**

 Quantian is a remastering of [Knoppix]("http://www.knopper.net/knoppix/index-en.html"), the self-configuring and directly bootable cdrom/dvd that turns any pc or laptop (provided it can boot from cdrom/dvd) into a full-featured Linux workstation. Quantian also incorporates [ clusterKnoppix]("http://bofh.be/clusterknoppix/") and adds support for [openMosix]("http://www.openmosix.org/"), including remote booting of light clients in an openMosix terminal server context. Earlier releases are still available; see below for URLs for downloads as well as ordering information.  Brief introductory information is available in a recent [paper published in *The Political Methodologist*]("http://dirk.eddelbuettel.com/papers/quantian-tpm.pdf"), slides from presentations at [ UseR! 2006]("http://dirk.eddelbuettel.com/papers/quantian_useR2006.pdf") (June 2006), [ DSC 2005]("http://dirk.eddelbuettel.com/papers/quantian_dsc2005.pdf") (August 2005), [ Usenix 2004]("http://dirk.eddelbuettel.com/papers/quantian_usenix2004_slides.pdf") (July 2004), and in the earlier [(revised) paper about Quantian]("http://dirk.eddelbuettel.com/papers/quantian_dsc2003.pdf") that has appeared in the [DSC 2003]("http://www.ci.tuwien.ac.at/Conferences/DSC-2003/") Proceedings. 
 Quantian is an extension of [Knoppix]("http://www.knopper.net/knoppix/index-en.html") and [ clusterKnoppix]("http://bofh.be/clusterknoppix/") from which it takes its base system of around gigabytes of software, along with fully automatic hardware detection and configuration. To this, it add about five gigabytes of software. 
**What does Quantian contain?**

 Quantian differs from Knoppix by adding a large number of programs of interest to applied or theoretical workers in quantitative or data-driven fields. The added quantitative, numerical or scientific programs comprise[LIST]
[*][R]("http://www.r-project.org/"), including *essentially all packages from CRAN* (excluding only non-Unix packages such as MimR, or ROracle which needs special headers and libraries) and BioConductor; the snapshot was made February 25, 2006) as well as some from other R package repositories, out-of-the box support for the powerful [ESS]("http://ess.r-project.org/") modes for [XEmacs]("http://www.xemacs.org/"), the [Ggobi visualisation program]("http://www.ggobi.org/"), the [Rpy]("http://rpy.sourceforge.net/") RPy Python interface, the [RSPerl]("http://www.omegahat.org/RSPerl") bi-directional integration with Perl, the award-winnning [JGR]("http://www.rosuda.org/JGR") Java GUI for R, the [Rserve]("http://www.rosuda.org/RServe") headless R server, the [Rpad interactive web interface]("http://www.rpad.org/") and initial support for the RKward gui for R.
[*]bioinformatics tools such *all packages from the [BioConductor project]("http://www.bioconductor.org/")*, as well as [bioperl]("http://bioperl.org/"), [biopython]("http://www.biopython.org/") and applications such as [blast2]("http://www.ncbi.nlm.nih.gov/BLAST/"), [clustalw]("http://www.ebi.ac.uk/clustalw/"), [ImageJ]("http://rsb.info.nih.gov/ij"),  and [hmmer]("http://hmmer.wustl.edu/");
[*][Octave]("http://www.octave.org/"), with add-on packages     [octave-forge]("http://octave.sourceforge.net/"), [octave-sp]("http://packages.debian.org/stable/math/octave-sp"),     [octave-epstk]("http://packages.debian.org/stable/math/octave-epstk"), [matwrap]("http://lnc.usc.edu/%7Eholt/matwrap/") and [ Inline::Octave]("http://search.cpan.org/dist/Inline-Octave/") as well as other matrix language environments;
[*]Computer-algebra systems [Maxima]("http://maxima.sf.net/") (including the X11 front-end and emacs support), [Pari/GP]("http://www.parigp-home.de/"), [GAP]("http://www-gap.dsc.st-and.ac.uk/%7Egap"), [GiNaC]("http://www.ginac.de/"), [YaCaS]("http://yacas.sf.net/"), [Axiom]("http://www.nongnu.org/axiom"), [Mathomatic]("http://mathomatic.orgserve.de/math/") and Calc;
[*][GSL]("http://sources.redhat.com/gsl"), the Gnu Scientific Library (GSL) including example binaries;
[*]the [QuantLib]("http://www.quantlib.org/") quantitative finance library including its Python interface;
[*]the [Grass]("http://grass.itc.it/") geographic information system;
[*]the [OpenDX]("http://www.opendx.org/") and [Mayavi]("http://mayavi.sf.net/") data visualisation systems;
[*][TeXmacs]("http://www.texmacs.org/") for wysiwyg scientific editing as well as [LyX]("http://www.lyx.org/") and [kile]("http://kile.sourceforge.net/") for wysiwyg (La)TeX editing;
[*]various [Python]("http://www.python.org/") modules including [Scientific and Numeric Python]("http://www.scipy.org/");
[*][Cernlib]("http://wwwasd.web.cern.ch/wwwasd/cernlib/"), a large number of programs and libraries from the [CERN]("http://cern.ch/") particle physic lab;
[*]the [bochs]("http://bochs.sourceforge.net/"), [wine]("http://www.winehq.com/") and [qemu]("http://fabrice.bellard.free.fr/qemu/") emulators;
[*]office suites such as [OpenOffice.org]("http://www.openoffice.org/") and [KOffice]("http://www.koffice.org/") as well as Abiword, Gnumeric and the Gimp;
[*]and various other programs such as [apcalc]("http://www.halcyon.com/ipscone/apcalc/overview.html"), [aplus]("http://www.aplusdev.org/"), [aribas]("http://www.mathematik.uni-muenchen.de/%7Eforster/sw/aribas.html"), [autoclass]("http://ic.arc.nasa.gov/ic/projects/bayes-group/autoclass/"), [DrGeo]("http://www.ofset.org/drgeo/"), [euler]("http://euler.sourceforge.net/"), [evolver]("http://www.susqu.edu/facstaff/b/brakke/evolver/"), [freefem]("http://www.ann.jussieu.fr/%7Ehecht/freefem++.htm"), [ ftnchek]("http://www.dsm.fordham.edu/%7Eftnchek/"), [gambit]("http://packages.debian.org/testing/math/gambit-doc"), [geg]("http://www.infolaunch.com/%7Edaveb/"), [geomview]("http://www.geomview.org/"), [ghemical]("http://www.uku.fi/%7Ethassine/ghemical/"), [glpk]("http://www.gnu.org/software/glpk/glpk.html"), [gnuplot]("http://www.gnuplot.info/"), [gperiodic]("http://gperiodic.seul.org/"), [gri]("http://gri.sourceforge.net/"), [gmt]("http://gmt.soest.hawaii.edu/"), [gretl]("http://gretl.sourceforge.net/"), [ImageMagick]("http://www.imagemagick.org/"), [IPE]("http://ipe.compgeom.org/"), [lam]("http://www.lam-mpi.org/"), [lp-solve]("http://packages.debian.org/stable/math/lp-solve"), [mcl]("http://packages.debian.org/unstable/math/mcl.html"), [mpich]("http://www-unix.mcs.anl.gov/mpi/mpich/"), [mpqc]("http://aros.ca.sandia.gov/%7Ecljanss/mpqc/"), [multimix]("http://packages.debian.org/unstable/math/multimix"), [rasmol]("http://www.umass.edu/microbio/rasmol/"), [plotutils]("http://www.gnu.org/software/plotutils/"), [pgapack]("http://www-fp.mcs.anl.gov/CCST/research/reports_pre1998/comp_bio/stalk/pgapack.html"), [pspp]("http://www.gnu.org/software/pspp/"), [pdl]("http://pdl.perl.org/"), [rcalc]("http://rcalc.sourceforge.net/"),  [SQLite]("http://www.sqlite.org/"), [Tclsh]("http://www.mkssoftware.com/docs/man1/tclsh.1.asp"), [yorick]("ftp://ftp-icf.llnl.gov/pub/Yorick/doc/index.html"), [xaos]("http://xaos.theory.org/"),  and [xppaut]("http://www.math.pitt.edu/%7Ebard/xpp/whatis.html");[/LIST]At the same time, all the distinguishing features that set Knoppix apart are retained in Quantian: [LIST]
[*]Auto-configuration of graphics, sound, disks, networking, auxiliary    devices which is second to none among computer installations
[*]A recent version (actually mostly 3.5 with some 3.4) of the [KDE desktop environment]("http://www.kde.org/")
[*]The GNU compiler suite comprising [gcc, g77, g++]("http://gcc.gnu.org/") compilers including gcj
[*][Perl]("http://www.perl.org/") and [Python]("http://www.python.org/") with loads of add-ons, plus other languages such [ruby]("http://www.ruby-lang.org/en/"), [tcl]("http://www.tcl.tk/"), [Lua]("http://www.lua.org/")...
[*]The [Emacs]("http://www.gnu.org/software/emacs/emacs.html") and [Vim]("http://www.vim.org/") editors, as well as [kate]("http://kate.kde.org/"), [jed]("http://www.jedsoft.org/jed/"), [joe]("http://freshmeat.net/projects/joe/"), [nedit]("http://www.nedit.org/") and [zile]("http://zile.sourceforge.net/")
[*][Gnumeric]("http://www.gnome.org/projects/gnumeric/"), [Koffice]("http://www.koffice.org/"), ... office tools, with [OpenOffice.org]("http://www.openoffice.org/") added back in
[*]A Swiss-army knife collection of networking tools allowing access    to wired and wireless lans, covering ethernet, isdn or dial-up modems
[*]And still in Quantian though no longer in Knoppix: a complete [teTeX]("http://www.tug.org/teTeX/") TeX / [LaTeX]("http://www.latex-project.org/") setup for scientific publishing along with wysiwyg frontends such as [kile]("http://kile.sourceforge.net/") and LyX / LyX-Qt, the preview mode for emacs editors, several additonal bibtex tools, and other goodies such as [prosper]("http://prosper.sourceforge.net/"), [pdfscreen]("http://sarovar.org/projects/pdfscreen/") and beamer for presentations as well as numerous Bibtex utilities.[/LIST]Last but not least, and thanks to [ clusterKnoppix]("http://bofh.be/clusterknoppix/"), quantian allows to build openMosix clusters in a matter of minutes -- and to immediately use them thanks to the 5 gb of added scientific software.         
 
**Screenshots**

 You can click on any of the images to see a full-size chart. The first screenshot shows version 0.3 with [openMosix]("http://www.openmosix.org/") running on a cluster with two computers, an [R]("http://www.r-project.org/") session (run from with [XEmacs]("http://www.xemacs.org/") using the [ESS mode]("http://ess.r-project.org/")) with lattice graphics, the [QuantLib]("http://www.quantlib.org/") demo 'BermudanSwaption' as well as [TeXmacs]("http://www.texmacs.org/") -- and the Knoppix 3.2 heritage is clearly visible on the background.
[CENTER] [[IMG]http://dirk.eddelbuettel.com/quantian/quantian_halfsize.jpeg[/IMG]]("http://dirk.eddelbuettel.com/quantian/quantian.jpeg") [/CENTER]
  The second screenshot shows Quantian version 0.4.9.3 with an openmosixview display of a three-node / four-cpu cluster as well as the [kile]("http://kile.sourceforge.net/") LaTeX frontend -- and the Knoppix 3.3 background image. 
[CENTER] [[IMG]http://dirk.eddelbuettel.com/quantian/quantian_0.4.9.2-halfsize.jpeg[/IMG]]("http://dirk.eddelbuettel.com/quantian/quantian_0.4.9.2.jpeg") [/CENTER]
  The third screenshot shows Quantian 0.5.9.2 with its new custom background which was contributed by Ed Pegg, Jr. Also shown are an R session running in an XEmacs buffer controlled by ESS. The R session displays a demo from Rmetrisc which displays the sensitivities of financial options to various parameters--the so-called 'greeks'--in a 3x2 display. Also shown is openMosixview. 
[CENTER] [[IMG]http://dirk.eddelbuettel.com/quantian/quantian_0.5.9.2-halfsize.jpeg[/IMG]]("http://dirk.eddelbuettel.com/quantian/quantian_0.5.9.2.jpeg") [/CENTER]
  
 
**Mailing lists**

 Two mailing lists exist for Quantian, courtesy of [Debian]("http://www.debian.org/")'s [Alioth]("http://alioth.debian.org/") host:[LIST]
[*][ quantian-announce]("http://lists.alioth.debian.org/pipermail/quantian-announce") for announcements only, very low volume, posting restricted to the listowner/maintainer
[*][ quantian-general]("http://lists.alioth.debian.org/pipermail/quantian-general") for general discussions about Quantian, posting restricted to subscribers -- so please subscribe before posting[/LIST]**Downloads**

      Two primary machines exist with Quantian archives:[LIST]
[*]The main archive is on the US West Coast is the         [Quantian archive at the         Fred Hutchinson Cancer Research Center]("http://quantian.fhcrc.org/") in Seattle (which replaces         for U of Washington mirror), and
[*]the backup archive on the US East Coast on         [         Greg Warnes' machine at Yale]("http://research.warnes.net/downloads/quantian/CURRENT/").[/LIST]The most current version is also on [Debian's Alioth site]("http://quantian.alioth.debian.org/").  Note that the increased filesize may create problems with web-caching software that can only handle files of up to 2 gb in size. It may be safer to use rsync or bittorrent instead of http webdownloads. 
 European mirrors site are available in [Madrid, Spain]("http://sunsite.rediris.es/mirror/quantian") at RedIRIS (also with [ftp access]("ftp://sunsite.rediris.es/mirror/quantian")) and [Aachen, Germany]("http://sunsite.informatik.rwth-aachen.de/ftp/pub/Linux/quantian/") at RWTH (also with [ftp access]("ftp://sunsite.informatik.rwth-aachen.de/pub/Linux/quantian/")). 
 **Rsync** access is available at the Fred Hutchinson archive.    
rsync rsync://quantian.fhcrc.org/quantian/    would retrieve a directory listing, and for example    rsync -v rsync://quantian.fhcrc.org/quantian/boot_0.6.9.x.iso .     would (verbosely) retrieve the 0.6.9.x-compatible boot image to the current directory.  **Bittorrent** A new torrent [is available]("http://www.tlm-project.org/public/distributions/quantian/") thanks to the [Linux Mirror Project]("http://www.tlm-project.org/"), as well as at [EpiGenomics (in Germany)]("http://finsen.epigenomics.net/%7Egurubert/"). U of Washington used to have both a bittorrent seeder and mirror with a nice graphical summary of usage, but that machine is currently, and for the foreseeable near-term future, unavailable.                
 
**Quantian for purchase**

 Quantian dvds and cdrom are available pre-made from the following third-party resellers:[LIST]
[*][ BudgetLinuxCDs.com]("http://www.budgetlinuxcds.com/index.php?page=Choose&letter=Q&sort=upd") has the dvd for $7.50 for the cdrom for $2.50.
[*][CheapBytes.com]("http://www.cheapbytes.com/") has the [dvd]("http://cart.cheapbytes.com/cgi-bin/cart/0070011119.html") for $11.99, and [ cdroms]("http://cart.cheapbytes.com/cgi-bin/cart/0070011023.html") from for $4.99 plus shipping.
[*][Frozentech.com]("http://www.frozentech.com/") has the most recent dvd at $1.99 with $0.49 shipping.
[*][LinCD.com]("http://lincd.com/") offers the [dvd]("http://lincd.com/product_info.php?cPath=22&products_id=33") for $2.99, and an older [cdrom]("http://lincd.com/product_info.php?cPath=22&products_id=34") release for $1.99.
[*][LinuxCentral.com]("http://www.linuxcentral.com/catalog/index.php3?prod_code=L000-539") lists 0.7.9.2 for $9.95.
[*][ ulnx.com]("http://ulnx.com/product_info.php?cPath=134&products_id=174&osCsid=0ccdfd30c62bca8b756a37a0632efbf2") has older Quantian cdroms for $2.29 plus shipping.
[*] In Australia, [lankum.com]("http://www.lankum.com/") offers Quantian [ cdroms for A$5.5]("http://www.lankum.com/store/catalog/product_info.php?products_id=232") and [ dvds for A$9.9]("http://www.lankum.com/store/catalog/product_info.php?products_id=377").
[*] In Germany, [BSDISO]("http://www.bsdiso.de/") offers Quantian cdroms premade for EUR 3.95 plus EUR 2 for shipping.[/LIST] I should note that I am not compensated by any of these vendors.  
 
**Comments**

 Please send comments, suggestions to the [ quantian-general]("http://lists.alioth.debian.org/pipermail/quantian-general") list. If your browser and mailer are configured correctly, then [EMAIL="quantian-general@lists.alioth.debian.org"]this link[/EMAIL] will open a new post.


---

### Post by RAV TUX on 2006-09-24
here are some Quantian screenshots I posted here:
[http://cafelinux.org/forums/index.php/topic,359.new.html#new](http://cafelinux.org/forums/index.php/topic,359.new.html#new)


> **yozef said:**
> [http://dirk.eddelbuettel.com/quantian.html](http://dirk.eddelbuettel.com/quantian.html)

just wondering if anybody is currently using Quantian?

            [IMG]http://dirk.eddelbuettel.com/images/trans.gif[/IMG]

---

### Post by RAV TUX on 2006-09-24
Xabacus on Quantian

---

### Post by rick_1010 on 2006-10-03
I'm wondering if you have Quantian installed to a hard drive or if you're running them all off of cd's... I've been driving myself insane the last few weeks trying to set up a functioning OpenMosix cluster, it seems that the project is unfortunately dying as its very difficult to impossible to get it to work on most distros since a kernel recompilation to an older kernel is always involved. Anyways, I am definately going to try Quantian and install it to hard drive to see how it works, I have tried ClusterKnoppix and I wasn't happy with the ability to install new software on it as I need to put some recent web development applications on the system.

---

### Post by rick_1010 on 2006-10-03
It seems that ClusterKnoppix basically died in 2004, is Quantian basically the continued effort of ClusterKnoppix? I really like that the latest version is from this year, I guess it makes sense that it would be more scienctific oriented as it seems that this is what most clusters are used for. However, I seem to be one of very few people who want to use one for something else, as I want to use it for web design development. Anyways, I'm excited to try this tomorrow and hopefully finally get a useable system up and running.

---

### Post by RAV TUX on 2006-10-04
> **rick_1010 said:**
> I'm wondering if you have Quantian installed to a hard drive or if you're running them all off of cd's... I've been driving myself insane the last few weeks trying to set up a functioning OpenMosix cluster, it seems that the project is unfortunately dying as its very difficult to impossible to get it to work on most distros since a kernel recompilation to an older kernel is always involved. Anyways, I am definately going to try Quantian and install it to hard drive to see how it works, I have tried ClusterKnoppix and I wasn't happy with the ability to install new software on it as I need to put some recent web development applications on the system.

I installed Quantian on my hard drive....when I test a Linux OS I test it on my Hard Drive. Doesn't do much use for me as a live CD.

---

### Post by willy[arg] on 2006-10-15
Hi. I'm new to EVERY UNIX based OS... mostly a dumb user... but I really want to try Quantian.... 
I already downloaded the "Quantian_0.7.9.2.iso" archive (2.7 Gb)... and also a file "miniknoppix_2005_EN.iso" that I read somewhere one can use to boot/install Quantian....
I want to Install Quantian in my SATA HD... I already have a SUSE version in its own HD partition ... (I did't do it, someone helped me) ... and Windows XP in another partition...

If y burn the Quantian.iso as a Boot DVD will it install Quantian on a third partition?  If not... please can anyone
help me do that?

Thanks
 (I do have a DVD burner)

Willy

---

### Post by RAV TUX on 2006-10-15
> **'willy[arg] said:**
> Hi. I'm new to EVERY UNIX based OS... mostly a dumb user... but I really want to try Quantian.... 
I already downloaded the "Quantian_0.7.9.2.iso" archive (2.7 Gb)... and also a file "miniknoppix_2005_EN.iso" that I read somewhere one can use to boot/install Quantian....
I want to Install Quantian in my SATA HD... I already have a SUSE version in its own HD partition ... (I did't do it, someone helped me) ... and Windows XP in another partition...

If y burn the Quantian.iso as a Boot DVD will it install Quantian on a third partition?  If not... please can anyone
help me do that?

Thanks
 (I do have a DVD burner)

Willy

Willy,

you only need the Quantian DVD, boot the live DVD and then just use your installer from there....

---

