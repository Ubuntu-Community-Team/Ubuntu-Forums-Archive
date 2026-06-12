---
title: "regular openoffice crash with 10.10"
date: 2011-02-22
forum: Desktop Environments
---

### Post by juju43 on 2011-02-22
Hello,

Since installing ubuntu 10.10 in january, my Openoffice (it seems mainly calc) regularly crashes. It always manage to keep file recovery active (even it's not always the latest). There is no really identified pattern except basically editing cells

my packages are currently:
ii  openoffice.org-base-core                                 1:3.2.1-7ubuntu1.1                                office product
ivity suite -- shared library
ii  openoffice.org-calc                                      1:3.2.1-7ubuntu1.1                                office product
ivity suite -- spreadsheet
ii  openoffice.org-common                                    1:3.2.1-7ubuntu1.1                                office product
ivity suite -- arch-independent files
ii  openoffice.org-core                                      1:3.2.1-7ubuntu1.1                                office product
ivity suite -- arch-dependent files
[...]

It seems there is also some 3.2.1-6ubuntu stuff
I use french localization in gnome environment if important

any ideas how to debug the problem ?
I just try to reset my preferences (move $HOME/.openoffice.org to .old) and I will see if it changes something.


Thanks

---

### Post by Hagar Delest on 2011-02-22
If no change, try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by svenofix on 2011-02-22
You could also try LibreOffice instead. I've been using it for some time now, no problems so far. The GTK integration is also great, provided you have the extra package installed (see bottom).

Not sure if they're in the official repositories for 10.10, but here's the commands to add and install LibreOffice:

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && sudo apt-get install libreoffice libreoffice-gtk libreoffice-gnome

---

### Post by Hagar Delest on 2011-02-23
PPA is not the official repository so beware. Better install from the LibO site (3.3.1 has just been released BTW).

---

### Post by dirtyhabanero on 2011-04-19
Yep, had some trouble trying to install via repository. Getting it from the Libre site. It also appears my netbook is on the cusp of minimum system requirements, this will be interesting.

Really sad to have to make the switch, I like using the Zotero plugin ...OpenOffice has just been driving me nuts and crashing for the last few weeks for no apparent reason. Anyone know anything about this? I'm running OpenOffice on Ubuntu 10.10 as well. I usually run it with Firefox in the background, could that be it?

Fingers crossed with the Libre install...

---

### Post by juju43 on 2011-04-19
I just tried with vanilla openoffice packages (3.3.0) with the same results.
I will also try LibreOffice

get deb from [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)

---

### Post by Hagar Delest on 2011-04-20
Have you reset the profile to be sure there is no leftover from previous versions.

---

### Post by juju43 on 2011-04-20
yes (mv ~/.openoffice.org ~/.openoffice.org.date)

---

### Post by Hagar Delest on 2011-04-21
Do you edit ODF files or MS Office files? You seem to use mostly Calc but it happens also with Writer, correct?

Perhaps you can try to change the tmp folder: create a dedicated folder in your home and set it in the Tools>Options>OOo>Paths dialog. Perhaps there is something interfering with the temporary files.

---

### Post by juju43 on 2011-04-26
editing ods file. I don't use enough writer in these past month to say it is also affected.

Same behavior with moving tmp dir or with LibreOffice 3.3

The code really seems to be the problem ...
I think I will need another compatible software ...

---

### Post by RamsesII on 2011-05-27
As far as I know LibreOffice is different from OpenOffice, they both use different source code though they look alike and do similar tasks. If you've been having the same issue with LibreOffice the problem shouldn't be in OpenOffice code but somewhere else maybe a common library they both use...

---

### Post by Hagar Delest on 2011-05-27
No, LibO and OOo are almost the same for the moment. Even for the Novell patches (from go-oo) have not been all integrated. But future versions may differ more and more. Especially with the code cleaning started for LibO.

---

### Post by juju43 on 2011-06-01
I worked on a text document a week ago and the problem also occurs quiet regularly.

Still don't know how to debug this, even if it is sending report to Oracle (which I'm not really sure to ever see feedback ...)

---

### Post by PatrickWiens on 2011-12-18
I'm having the same problem!
Using Libre Office 3.4.4 on a Ubuntu 11.10. My native language is Portuguese-BR.
I haven't got a clue of what's going on - in unespecific situations, it just closes out of nowhere. I get it very often when copying and pasting, but sometimes it happens without doing anything.

---

