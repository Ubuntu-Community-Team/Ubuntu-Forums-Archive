---
title: "TexLive Install error messages"
date: 2010-04-24
forum: Education &amp; Science
---

### Post by roderickf on 2010-04-24
I am a new ubuntu user. I want to use tex and I installed TexLive on my ubuntu9.10, by running
```
sudo apt-get install texlive
```and also gedit latex plugin
```
sudo apt-get install gedit-latex-plugin
```But I get error message:
```
Setting up tex-common (1.20) ...
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.8); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dvipdfmx:
 dvipdfmx depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing dvipdfmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on tex-commoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                  No apport report written because MaxReports is reached already
                                                                                                                                                No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                                                                                                    No apport report written because MaxReports is reached already
                                                                                                                                                                  No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                                                                                                      No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                                                                                                        n (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2007); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-base depends on texlive-base-bin (>= 2007-13); however:
  Package texlive-base-bin is not configured yet.
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 1.18); however:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                              Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-generic-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-generic-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2007-11); however:
No apport report written because MaxReports is reached already

                                                               texlive-pstricks depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rubber:
 rubber depends on texlive-latex-base | tetex-bin; however:
  Package texlive-latex-base is not configured yet.
  Package tetex-bin is not installed.
dpkg: error processing rubber (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-11); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-base-bin-doc:
 texlive-base-bin-doc depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base-bin-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-extra-utils depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-fonts-recommended-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-latex-base-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
 texlive-pstricks-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
 tipa depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gedit-latex-plugin:
 gedit-latex-plugin depends on rubber; however:
  Package rubber is not configured yet.
dpkg: error processing gedit-latex-plugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tex-common
 texlive-common
 texlive-base-bin
 dvipdfmx
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 lmodern
 texlive-generic-recommended
 texlive-pstricks
 prosper
 rubber
 texlive-fonts-recommended
 texlive
 texlive-base-bin-doc
 texlive-extra-utils
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-pstricks-doc
 tipa
 gedit-latex-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```And I get this message every time i install something.
What is this about? What shall I do?

---

### Post by SnickerSnack on 2010-04-24
It appears that the only problem is this:

```
Setting up tex-common (1.20) ...
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
```

and the other problems stem from it because:

> This package contains a number of scripts and common configuration files that are needed to install a TeX System.

Try installing just tex-common, and see if you still get an error.  Maybe such an error will give more information.

---

### Post by roderickf on 2010-04-24
Thanks SnickerSnack! Everything solved.

---

### Post by SnickerSnack on 2010-04-24
> **roderickf said:**
> Thanks SnickerSnack! Everything solved.

No problemo.  Be sure to mark the thread as solved using the Thread Tools.

---

### Post by calbaker on 2010-09-30
I'm now getting the following errors when I try to install texlive or anything that depends on texlive:
 
> 
E: tex-common: subprocess installed post-installation script returned error exit status 1
E: texlive-pstricks: dependency problems - leaving unconfigured
E: asymptote: dependency problems - leaving unconfigured
E: texlive-latex-recommended: dependency problems - leaving unconfigured
E: latex-xcolor: dependency problems - leaving unconfigured
E: pgf: dependency problems - leaving unconfigured
E: latex-beamer: dependency problems - leaving unconfigured
E: prosper: dependency problems - leaving unconfigured
E: texlive-extra-utils: dependency problems - leaving unconfigured
E: texlive-font-utils: dependency problems - leaving unconfigured
E: texlive-fonts-recommended: dependency problems - leaving unconfigured
E: texlive-pictures: dependency problems - leaving unconfigured
E: texlive-latex-extra: dependency problems - leaving unconfigured
E: texlive-luatex: dependency problems - leaving unconfigured
E: tipa: dependency problems - leaving unconfigured
E: texlive-latex-base: dependency problems - leaving unconfigured
E: texlive-generic-recommended: dependency problems - leaving unconfigured



I have completely removed and then reinstalled texlive to no avail.  I also have the ctan texlive installed to /usr/local/texlive/2010/, and it's working within terminal, but it doesn't function with LyX, TexMaker, or auctex+emacs.  

Thoughts?

---

### Post by calbaker on 2010-10-01
It hasn't been resolved for me.  What am I doing wrong?

---

### Post by Rallg on 2010-10-07
Not working for me either. Tried every trick I know, searched the forum, etc.

This has been happening for at least two weeks.

---

### Post by spurs21 on 2010-10-21
Wow, this sucks. texlive can't install on Lucid either. I have to dump this operating system ASAP if I can't use latex.

---

### Post by mustail on 2010-10-26
I did not have any problem with TeXLive 2009 with Ubuntu 10.04 Lucid. Now that I have switched to 10.10 Maverick, I cannot install TexLive 2009 properly.. I get the similar error report that is quoted above. It seems to be related with tex-common package, and all other stuff related to it is not configured properly.. I think this is an important bug.

---

### Post by gb38 on 2011-01-02
I had a similar problem during upgrade from 10.04 lucid to 10.10 maverick: during each trial dist-upgrade the process stuck on one file of 100KB. This appeared to be texlive-common 2009-10.
I solved this by 
1) use synaptic instead of dist-upgrade
2) unmark this in synaptic and perform the upgrade anyway
3) manually download the required file and the 2009-11 file from [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-common_2009-11_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-common_2009-11_all.deb)
4) in synaptic I added the downloaded packages (there is a menu option for that)

---

### Post by Axolotl9250 on 2011-01-02
I don't Think I have the problem and I have latest Ubuntu. However, I never explicitly install texlive, rather, I install lyx and then have the required latex stuff get installed with it as deps, and I don't get errors. Maybe worth a shot.

---

### Post by elkr on 2012-05-04
I've experienced the same problem: purging the complaining packages and reinstalling texlive-common helped. 

Anyway, this is only to have LyX. Texlive in Ubuntu is infamously outdated, so I recommend everybody to install it directly from: [http://www.tug.org/texlive]("http://www.tug.org/texlive;") - the newest version has a lot more features in packages, as well as bug fixes. They also have a network installer that installs everything with one command to, say, /usr/local/texlive; all you need to do then is set PATH.

---

