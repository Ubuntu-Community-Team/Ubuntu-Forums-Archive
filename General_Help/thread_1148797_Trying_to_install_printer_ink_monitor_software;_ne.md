---
title: "Trying to install printer ink monitor software; need advice."
date: 2009-05-04
forum: General Help
---

### Post by GARoss on 2009-05-04
For those of you that are knowledgeable about printer software, I need some advice. I've downloaded drivers & software for older Canon printers & have had success installing the drivers for both amd64 (forced) & i386. But the printer monitor is where I'm stuck, so, I'm hoping someone might be able to advise me how to finish this install of Canon Linux printer ink monitor. 
Below is a terminal transcript of the install of bjcupsmon-2.2-2 which is incomplete. My experience installing the drivers was that many of the support software has been updated so pointers had to be made from the old to the current to get things to work. I'm sure that is some of the problem now.
([ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/))
As I am not sharp as a tack with computer programming I'm not sure what to do next. The last 5 paragraphs, in bold type, asks for AM_GNU_GETTEXT & update po/Makevars & more.
Anyway, I'm hoping someone might have some knowledge of these things or have contacts that do.
BTW. I realize that there are programs like *Ink & Inkblot*, they both work to an extent with my i950 Canon. But, I'd like to see if this will work.
I'd appreciate any suggestions offered.
Regards,
GARoss

[I]george@jauntygeorge-desktop:~/bjcupsmon-2.2-2$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running gettextize... Ignore non-fatal messages.
Copying file ABOUT-NLS
Copying file config.rpath
Not copying intl/ directory.
Copying file po/Makefile.in.in
Copying file po/Makevars.template
Copying file po/Rules-quot
Copying file po/boldquot.sed
Copying file po/en@boldquot.header
Copying file po/en@quot.header
Copying file po/insert-header.sin
Copying file po/quot.sed
Copying file po/remove-potcdate.sin
Adding an entry to po/ChangeLog (backup is in po/ChangeLog~)
Creating directory m4
Copying file m4/gettext.m4
Copying file m4/iconv.m4
Copying file m4/lib-ld.m4
Copying file m4/lib-link.m4
Copying file m4/lib-prefix.m4
Copying file m4/nls.m4
Copying file m4/po.m4
Copying file m4/progtest.m4
Creating m4/ChangeLog
Updating Makefile.am (backup is in Makefile.am~)
Updating configure.in (backup is in configure.in~)
Adding an entry to ChangeLog (backup is in ChangeLog~)

[B]Please use AM_GNU_GETTEXT([external]) in order to cause autoconfiguration
to look for an external libintl.

Please update po/Makevars so that it defines all the variables mentioned
in po/Makevars.template.
You can then remove po/Makevars.template.

Please run 'aclocal -I m4' to regenerate the aclocal.m4 file.
You need aclocal from GNU automake 1.9 (or newer) to do this.
Then run 'autoconf' to regenerate the configure file.

You will also need config.guess and config.sub, which you can get from the CVS
of the 'config' project at [http://savannah.gnu.org/](http://savannah.gnu.org/). The commands to fetch them
are
$ wget 'http://savannah.gnu.org/cgi-bin/viewcvs/*checkout*/config/config/config.guess'
$ wget 'http://savannah.gnu.org/cgi-bin/viewcvs/*checkout*/config/config/config.sub'

You might also want to copy the convenience header file gettext.h
from the /usr/share/gettext directory into your package.
It is a wrapper around <libintl.h> that implements the configure --disable-nls
option.

Press Return to acknowledge the previous five paragraphs.[/B][/I]

---

### Post by ellgor on 2009-05-05
Hi,

Try Qink, from the repos.

Regards, Ellgor.

---

### Post by GARoss on 2009-05-05
> **ellgor said:**
> Hi,

Try Qink, from the repos.

Regards, Ellgor.

Thanks, Ellgor
Like I said in my post, Ink, Inkblot & now Qink do work - at least partially. Ink is launched in the terminal & shows all 6 ink levels. The problem is the labels are not in order & not labeled correctly. This could be figured out in time. Inkblot & Qink show 4 out of 6. I'd have to work with them a bit to see if they are labeled correctly.
Still, it would be nice to get the actual software working.

---

