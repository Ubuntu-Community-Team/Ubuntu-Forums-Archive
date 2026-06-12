---
title: "Can't upgrade OpenOffice..."
date: 2006-08-31
forum: Desktop Environments
---

### Post by Anduu on 2006-08-31
Well this is the first time i have had problems upgrading anything...

Synaptic is showing a bunch of openoffice upgrades.Here is what happens when I try:
```

anduu@AthlonXP2200PlusViaASUS:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-us
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-writer
  python-uno ttf-opensymbol
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/89.6MB of archives.
After unpacking, 26.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 130460 files and directories currently installed.)
Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12.1 (using .../openoffice.org-calc_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/scalc.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-writer 2.0.2-2ubuntu12.1 (using .../openoffice.org-writer_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-writer_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/swriter.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-draw 2.0.2-2ubuntu12.1 (using .../openoffice.org-draw_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-draw_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/sdraw.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-impress 2.0.2-2ubuntu12.1 (using .../openoffice.org-impress_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-impress_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/simpress.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-math 2.0.2-2ubuntu12.1 (using .../openoffice.org-math_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-math ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-math_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/smath.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-base 2.0.2-2ubuntu12.1 (using .../openoffice.org-base_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-base ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-base_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/sdatabase.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-calc_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-writer_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-draw_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-impress_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-math_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-base_2.0.3-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
anduu@AthlonXP2200PlusViaASUS:~$
```

No luck with dist-upgrade or apt-get -f install.

Any ideas?

---

### Post by lonedar on 2006-08-31
I'm having the same problem. I think that it has got something to do with both en_us and en_gb files being installed.

---

### Post by Uncle Spellbinder on 2006-08-31
I'm only seeing 2.0.2 as available. What repo are you guys using to find these updates?

---

### Post by Anduu on 2006-08-31
Dammit I knew it...I only posted my problem last night because it was late and I didn't have time to troubleshoot it...

If you are using the custom repo "deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) dapper universe multiverse" comment it out and everything is back to normal.

I have about had it up to here with custom repos messing around with my core Ubuntu stuff.

---

### Post by be4truth on 2007-01-21
try this one for dapper.
[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)
works fine with me!

---

