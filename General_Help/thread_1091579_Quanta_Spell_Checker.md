---
title: "Quanta Spell Checker"
date: 2009-03-09
forum: General Help
---

### Post by cong06 on 2009-03-09
I'm having problems getting the spell checker to work.
I searched on the internet, and I found this link:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119934.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119934.html)

Following through the steps:
**locate aspell**
```

/etc/apparmor.d/abstractions/aspell
/usr/bin/aspell
/usr/bin/aspell-import
/usr/bin/run-with-aspell
/usr/lib/aspell
/usr/lib/libaspell.so.15
/usr/lib/libaspell.so.15.1.4
/usr/lib/aspell/american-w_accents.alias
/usr/lib/aspell/american-wo_accents.alias
/usr/lib/aspell/american.alias
/usr/lib/aspell/british-ise-w_accents.alias
/usr/lib/aspell/british-ise-wo_accents.alias
/usr/lib/aspell/british-ise.alias
/usr/lib/aspell/british-ize-w_accents.alias
/usr/lib/aspell/british-ize-wo_accents.alias
/usr/lib/aspell/british-ize.alias
/usr/lib/aspell/british-w_accents.alias
/usr/lib/aspell/british-wo_accents.alias
/usr/lib/aspell/british.alias
/usr/lib/aspell/canadian-w_accents.alias
/usr/lib/aspell/canadian-wo_accents.alias
/usr/lib/aspell/canadian.alias
/usr/lib/aspell/ccpp.amf
/usr/lib/aspell/comment.amf
/usr/lib/aspell/context-filter.info
/usr/lib/aspell/context-filter.la
/usr/lib/aspell/context-filter.so
/usr/lib/aspell/cp1250.cmap
/usr/lib/aspell/cp1250.cset
/usr/lib/aspell/cp1251.cmap
/usr/lib/aspell/cp1251.cset
/usr/lib/aspell/cp1252.cmap
/usr/lib/aspell/cp1252.cset
/usr/lib/aspell/cp1253.cmap
/usr/lib/aspell/cp1253.cset
/usr/lib/aspell/cp1254.cmap
/usr/lib/aspell/cp1254.cset
/usr/lib/aspell/cp1255.cmap
/usr/lib/aspell/cp1255.cset
/usr/lib/aspell/cp1256.cmap
/usr/lib/aspell/cp1256.cset
/usr/lib/aspell/cp1257.cmap
/usr/lib/aspell/cp1257.cset
/usr/lib/aspell/cp1258.cmap
/usr/lib/aspell/cp1258.cset
/usr/lib/aspell/debctrl-filter.info
/usr/lib/aspell/debctrl-filter.la
/usr/lib/aspell/debctrl-filter.so
/usr/lib/aspell/debctrl.amf
/usr/lib/aspell/dvorak.kbd
/usr/lib/aspell/email-filter.info
/usr/lib/aspell/email-filter.la
/usr/lib/aspell/email-filter.so
/usr/lib/aspell/email.amf
/usr/lib/aspell/en-common.rws
/usr/lib/aspell/en-variant_0.multi
/usr/lib/aspell/en-variant_0.rws
/usr/lib/aspell/en-variant_1.multi
/usr/lib/aspell/en-variant_1.rws
/usr/lib/aspell/en-variant_2.multi
/usr/lib/aspell/en-variant_2.rws
/usr/lib/aspell/en-w_accents.multi
/usr/lib/aspell/en-wo_accents.multi
/usr/lib/aspell/en.dat
/usr/lib/aspell/en.multi
/usr/lib/aspell/en_CA-w_accents-only.rws
/usr/lib/aspell/en_CA-w_accents.multi
/usr/lib/aspell/en_CA-wo_accents-only.rws
/usr/lib/aspell/en_CA-wo_accents.multi
/usr/lib/aspell/en_CA.multi
/usr/lib/aspell/en_GB-ise-w_accents-only.rws
/usr/lib/aspell/en_GB-ise-w_accents.multi
/usr/lib/aspell/en_GB-ise-wo_accents-only.rws
/usr/lib/aspell/en_GB-ise-wo_accents.multi
/usr/lib/aspell/en_GB-ise.multi
/usr/lib/aspell/en_GB-ize-w_accents-only.rws
/usr/lib/aspell/en_GB-ize-w_accents.multi
/usr/lib/aspell/en_GB-ize-wo_accents-only.rws
/usr/lib/aspell/en_GB-ize-wo_accents.multi
/usr/lib/aspell/en_GB-ize.multi
/usr/lib/aspell/en_GB-w_accents.multi
/usr/lib/aspell/en_GB-wo_accents.multi
/usr/lib/aspell/en_GB.multi
/usr/lib/aspell/en_US-w_accents-only.rws
/usr/lib/aspell/en_US-w_accents.multi
/usr/lib/aspell/en_US-wo_accents-only.rws
/usr/lib/aspell/en_US-wo_accents.multi
/usr/lib/aspell/en_US.multi
/usr/lib/aspell/en_affix.dat
/usr/lib/aspell/en_phonet.dat
/usr/lib/aspell/english-variant_0.alias
/usr/lib/aspell/english-variant_1.alias
/usr/lib/aspell/english-variant_2.alias
/usr/lib/aspell/english-w_accents.alias
/usr/lib/aspell/english-wo_accents.alias
/usr/lib/aspell/english.alias
/usr/lib/aspell/html-filter.info
/usr/lib/aspell/html.amf
/usr/lib/aspell/iso-8859-1.cmap
/usr/lib/aspell/iso-8859-1.cset
/usr/lib/aspell/iso-8859-10.cmap
/usr/lib/aspell/iso-8859-10.cset
/usr/lib/aspell/iso-8859-11.cmap
/usr/lib/aspell/iso-8859-11.cset
/usr/lib/aspell/iso-8859-13.cmap
/usr/lib/aspell/iso-8859-13.cset
/usr/lib/aspell/iso-8859-14.cmap
/usr/lib/aspell/iso-8859-14.cset
/usr/lib/aspell/iso-8859-15.cmap
/usr/lib/aspell/iso-8859-15.cset
/usr/lib/aspell/iso-8859-16.cmap
/usr/lib/aspell/iso-8859-16.cset
/usr/lib/aspell/iso-8859-2.cmap
/usr/lib/aspell/iso-8859-2.cset
/usr/lib/aspell/iso-8859-3.cmap
/usr/lib/aspell/iso-8859-3.cset
/usr/lib/aspell/iso-8859-4.cmap
/usr/lib/aspell/iso-8859-4.cset
/usr/lib/aspell/iso-8859-5.cmap
/usr/lib/aspell/iso-8859-5.cset
/usr/lib/aspell/iso-8859-6.cmap
/usr/lib/aspell/iso-8859-6.cset
/usr/lib/aspell/iso-8859-7.cmap
/usr/lib/aspell/iso-8859-7.cset
/usr/lib/aspell/iso-8859-8.cmap
/usr/lib/aspell/iso-8859-8.cset
/usr/lib/aspell/iso-8859-9.cmap
/usr/lib/aspell/iso-8859-9.cset
/usr/lib/aspell/koi8-r.cmap
/usr/lib/aspell/koi8-r.cset
/usr/lib/aspell/koi8-u.cmap
/usr/lib/aspell/koi8-u.cset
/usr/lib/aspell/none.amf
/usr/lib/aspell/nroff-filter.info
/usr/lib/aspell/nroff-filter.la
/usr/lib/aspell/nroff-filter.so
/usr/lib/aspell/nroff.amf
/usr/lib/aspell/perl.amf
/usr/lib/aspell/sgml-filter.info
/usr/lib/aspell/sgml-filter.la
/usr/lib/aspell/sgml-filter.so
/usr/lib/aspell/sgml.amf
/usr/lib/aspell/split.kbd
/usr/lib/aspell/standard.kbd
/usr/lib/aspell/tex-filter.info
/usr/lib/aspell/tex-filter.la
/usr/lib/aspell/tex-filter.so
/usr/lib/aspell/tex.amf
/usr/lib/aspell/texinfo-filter.info
/usr/lib/aspell/texinfo-filter.la
/usr/lib/aspell/texinfo-filter.so
/usr/lib/aspell/texinfo.amf
/usr/lib/aspell/u-deva.cmap
/usr/lib/aspell/u-deva.cset
/usr/lib/aspell/url.amf
/usr/lib/enchant/libenchant_aspell.so
/usr/lib/kde3/kspell_aspell.la
/usr/lib/kde3/kspell_aspell.so
/usr/sbin/aspell-autobuildhash
/usr/sbin/update-default-aspell
/usr/sbin/update-dictcommon-aspell
/usr/share/aspell
/usr/share/apps/quanta/dtep/php/aspell.tag
/usr/share/aspell/aspell.compat
/usr/share/aspell/en-common.cwl.gz
/usr/share/aspell/en-variant_0.cwl.gz
/usr/share/aspell/en-variant_1.cwl.gz
/usr/share/aspell/en-variant_2.cwl.gz
/usr/share/aspell/en.contents
/usr/share/aspell/en_CA-w_accents-only.cwl.gz
/usr/share/aspell/en_CA-wo_accents-only.cwl.gz
/usr/share/aspell/en_GB-ise-w_accents-only.cwl.gz
/usr/share/aspell/en_GB-ise-wo_accents-only.cwl.gz
/usr/share/aspell/en_GB-ize-w_accents-only.cwl.gz
/usr/share/aspell/en_GB-ize-wo_accents-only.cwl.gz
/usr/share/aspell/en_US-w_accents-only.cwl.gz
/usr/share/aspell/en_US-wo_accents-only.cwl.gz
/usr/share/doc/aspell
/usr/share/doc/aspell-en
/usr/share/doc/libaspell15
/usr/share/doc/aspell/NEWS.Debian.gz
/usr/share/doc/aspell/README.Debian
/usr/share/doc/aspell/README.gz
/usr/share/doc/aspell/TODO
/usr/share/doc/aspell/changelog.Debian.gz
/usr/share/doc/aspell/changelog.gz
/usr/share/doc/aspell/changelog.html.gz
/usr/share/doc/aspell/copyright
/usr/share/doc/aspell/examples
/usr/share/doc/aspell/examples/ispell
/usr/share/doc/aspell/examples/spell
/usr/share/doc/aspell-en/README.gz
/usr/share/doc/aspell-en/SCOWL-README.gz
/usr/share/doc/aspell-en/changelog.Debian.gz
/usr/share/doc/aspell-en/changelog.gz
/usr/share/doc/aspell-en/copyright
/usr/share/doc/libaspell15/NEWS.Debian.gz
/usr/share/doc/libaspell15/README.gz
/usr/share/doc/libaspell15/TODO
/usr/share/doc/libaspell15/changelog.Debian.gz
/usr/share/doc/libaspell15/changelog.gz
/usr/share/doc/libaspell15/changelog.html.gz
/usr/share/doc/libaspell15/copyright
/usr/share/doc/libenchant1c2a/aspell
/usr/share/doc/libenchant1c2a/aspell/README
/usr/share/lintian/overrides/aspell
/usr/share/locale-langpack/en_GB/LC_MESSAGES/aspell.mo
/usr/share/man/man1/aspell-import.1.gz
/usr/share/man/man1/aspell.1.gz
/usr/share/man/man1/run-with-aspell.1.gz
/usr/share/man/man8/aspell-autobuildhash.8.gz
/usr/share/man/man8/update-default-aspell.8.gz
/usr/share/man/man8/update-dictcommon-aspell.8.gz
/usr/share/services/kspell_aspell.desktop
/var/cache/dictionaries-common/aspell.db
/var/lib/aspell
/var/lib/aspell/en-common.rws
/var/lib/aspell/en-variant_0.rws
/var/lib/aspell/en-variant_1.rws
/var/lib/aspell/en-variant_2.rws
/var/lib/aspell/en.compat
/var/lib/aspell/en_CA-w_accents-only.rws
/var/lib/aspell/en_CA-wo_accents-only.rws
/var/lib/aspell/en_GB-ise-w_accents-only.rws
/var/lib/aspell/en_GB-ise-wo_accents-only.rws
/var/lib/aspell/en_GB-ize-w_accents-only.rws
/var/lib/aspell/en_GB-ize-wo_accents-only.rws
/var/lib/aspell/en_US-w_accents-only.rws
/var/lib/aspell/en_US-wo_accents-only.rws
/var/lib/dictionaries-common/aspell
/var/lib/dictionaries-common/aspell/aspell-en
/var/lib/dpkg/info/aspell-en.list
/var/lib/dpkg/info/aspell-en.md5sums
/var/lib/dpkg/info/aspell-en.postinst
/var/lib/dpkg/info/aspell-en.postrm
/var/lib/dpkg/info/aspell.list
/var/lib/dpkg/info/aspell.md5sums
/var/lib/dpkg/info/aspell.postinst
/var/lib/dpkg/info/libaspell15.list
/var/lib/dpkg/info/libaspell15.md5sums
/var/lib/dpkg/info/libaspell15.postinst
/var/lib/dpkg/info/libaspell15.postrm
/var/lib/dpkg/info/libaspell15.shlibs
```
**dpkg -s aspell**
```

Package: aspell
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 1160
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.60.6-1
Replaces: aspell-bin (<< 0.60.3-2), aspell-hi (<= 0.01-1), aspell-mr (<= 0.10-1)
Provides: aspell-bin
Depends: libaspell15 (= 0.60.6-1), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libncursesw5 (>= 5.6+20071006-3), libstdc++6 (>= 4.1.1), dictionaries-common (>> 0.40)
Recommends: aspell-en | aspell-dictionary | aspell6a-dictionary
Suggests: aspell-doc, spellutils
Conflicts: aspell-bin (<< 0.60.3-2)
Description: GNU Aspell spell-checker
 GNU Aspell is a spell-checker which can be used either as a standalone
 application or embedded in other programs.  Its main feature is that it
 does a much better job of suggesting possible spellings than just about
 any other spell-checker available for the English language, including
 Ispell and Microsoft Word.  It also has many other technical
 enhancements over Ispell such as using shared memory for dictionaries
 and intelligently handling personal dictionaries when more than one
 Aspell process is open at once.
 .
 Aspell is designed to be a drop-in replacement for Ispell.
Original-Maintainer: Brian Nelson <pyro@debian.org>
Homepage: http://aspell.net/

```

Personally I feel like the only thing that I need to do is go in and tell Quanta where aspell is, but I don't know where that setting is.
The only thing I found was "Settings > configure Editor > Plugins" and I checked "KDataTool Plugin" which is supposed to handle spell check check (if installed).
```
apt-get install kdatatool
``` comes up with nothing.

Where do you set it up?

---

### Post by cong06 on 2009-04-17
I went through the steps at
[https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119934.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119934.html)
and 
[https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119941.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119941.html)

Installed a bunch of dependencies, but for the most part they were all there (using ldd /usr/bin aspell found some files). And it still won't work.



So, a google search comes up with this thread:
[http://linux.derkeiler.com/Mailing-Lists/Debian/2006-05/msg03280.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-05/msg03280.html)

Which points out that the only way to fix it is to change "quantarc" since quanta has no Gui (that'll save me quite a bit of time)

But copying and pasting the recommended code for quantarc:
```
[Spelling]
Client=1
DictFromList=true
Dictionary=en
Encoding=0
IgnoreList=
NoRootAffix=false
ReplaceAllList=
RunTogether=false
```
doesn't fix it, and I don't know where in that it's pointing to aspell...
Trying: ```
Path=/usr/bin/aspell
``` didn't work even if it seems like it should since the error is:
```
The spelling program could not be started. Please make sure you have
set the correct spelling program and that it is properly configured and
in your PATH.
```
hinting at a variable "PATH" that needs to be set.

---

### Post by texastwister on 2009-06-18
Found a solution that solved this for me at [http://newyork.ubuntuforums.org/showthread.php?t=600772&page=2](http://newyork.ubuntuforums.org/showthread.php?t=600772&page=2)

Added this text block:

```
[KSpell]
KSpell_Client=1
KSpell_DictFromList=1
KSpell_Dictionary=american	
KSpell_Encoding=0
KSpell_NoRootAffix=0
KSpell_RunTogether=0
```
	
to the file: ~/.kde/share/config/kdeglobals 

Once that change was made, spell checking worked in Quanta -- without even requiring a restart of Quanta.

Hope that helps...

Scott

---

### Post by texastwister on 2009-06-18
Found a solution that solved this for me at [http://newyork.ubuntuforums.org/showthread.php?t=600772&page=2](http://newyork.ubuntuforums.org/showthread.php?t=600772&page=2)

Added this text block:

	[KSpell]
	KSpell_Client=1
	KSpell_DictFromList=1
	KSpell_Dictionary=american	
	KSpell_Encoding=0
	KSpell_NoRootAffix=0
	KSpell_RunTogether=0
	
to the file: ~/.kde/share/config/kdeglobals 

Once that change was made, spell checking worked in Quanta -- without even requiring a restart of Quanta.

---

### Post by RuralHack on 2011-06-03
This is the solution. Do this one.

---

### Post by churlishbeaver on 2011-08-19
Thanks, Texastwister.  That worked brilliantly for me (although I still need to see if I can make it work with an Australian English, rather than an Amercan English dictionary).  Thank you also Cong06 for having taken the trouble to post your query here and to others who have responded.

The time and effort necessary to explain the technical problem and ask for suggested solutions is what has stopped me for years from seeking solutions to a considerable number of Linux problems that I have lived with.

Quanta is a brilliant piece of software and I think it would take the world by storm if less technically able people were able to install it close to as easily as it is now possible to install other web publishing programs (mostly proprietary commercial programs).

Although Quanta is brilliant, I have lived (I think maybe for 6 or 7 years now), and still do, with limitations which stop me from making full use of its capabilities. The story is the same with me for many Linux open source packages.

(BTW, I think it would be great if Quanta could be interfaced to work with web-sites content managed with Drupal, Joomla, etc.) 

I consider myself technically able having worked as an applications programmer (including on one very complex distributed Java application for 2 years once), but, for at least the last 9 years, I have found that it takes too much time and energy (not having to be able to talk with technically skilled people in the same room as me about technical problems) to find solutions to Linux problems, so I usually don't bother and just live with the limitations.

I think if the producers and maintainers of technical software were to find ways to help people like me overcome the difficulties I have had with Linux, a way to get more people who think that they have no choice but to continue to use proprietary (particularly M$) software would be found.

A NEW BUSINESS MODEL NEEDED FOR THE FAIR REMUNERATION OF OPEN SOURCE 

I also think that a more effective business model, that would allow producers and maintainers of Open Source software, particularly quanta, to be fairly paid for their work is needed. It seems that too many open source programmers are paid too little for the valuable work they do. (With all that computer users are likely to save from no longer having to pay M$, most would need little persuasion to begin to start to fairly pay open source programmers for their work,)

I have in mind an idea for one based on MICRO-PAYMEMTS. In some ways it would be like flatter (see [http://flattr.com/](http://flattr.com/)), but I think it can be made far more flexible and at least as easy for payers and payees to use.  I think the kind of system I have in mind is likely to be far more widely used than what is now on offer. I am not sure how much time and energy I can put into this, but if anyone would like to help me with this, please leave a note here (perhaps with a suggestion of a more suitable place to discuss this).

---

