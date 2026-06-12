---
title: "Can't get firefox extensions page"
date: 2005-05-21
forum: Desktop Environments
---

### Post by [censored] on 2005-05-21
[https://addons.mozilla.org/extensions/](https://addons.mozilla.org/extensions/)

This refers me to another page, telling me to upgrade my version of firefox.

Should I download the source package, and install as root ... using firefox's custom installer? Or will that screw up my package management system?

---

### Post by f.prisson on 2005-05-21
If you have a version < 1.0.4 this thread might be interesting for you:

[http://ubuntuforums.org/showthread.php?t=34242&highlight=mozilla+extension](http://ubuntuforums.org/showthread.php?t=34242&highlight=mozilla+extension)

---

### Post by jasmuz on 2005-05-21
[QUOTE='[censored]'][https://addons.mozilla.org/extensions/](https://addons.mozilla.org/extensions/)

This refers me to another page, telling me to upgrade my version of firefox.

Should I download the source package, and install as root ... using firefox's custom installer? Or will that screw up my package management system?[/QUOTE]
 My best recomendation is to add the Ubuntu Backports.
[www.backports.ubuntuforums.org](www.backports.ubuntuforums.org) [HOWTO]
They have already backported Mozilla Firefox 1.0.4

---

### Post by lorap on 2005-05-22
hi friend!
why wouldn't you just upgrade your version?
let's do it together.
first of all download it to your, say, desktop.
then place a mouse over it and press right button.
from the list choose the option ""extract here" after what you'll see a new directory created with all files in it needed for upgrade.
now delete the archive cause don't need it anymore.
double click on the new directory's been created from archive.
once you get it open you'll see some directory inside it. cut that directory and paste it to the desktop. now after you cut the directory the old one became an empty. delete it also. double click on the directory you've paste on the desktop and watch the files inside.
you should see a file called "install mozilla" or "install script".
open a terminal window and write:

sudo sh

then place a mouce over the install script press the small button and grab it to the terminal window then press enter.
the install precess'll begin immidiatly.
remember friend!
to overrite your old firefox-mozilla directory when asked to choose the directory to install to choose "custom" and write in the path "/usr/lib/mozilla-firefox".
after what you'll be prompted to delete the old one press "ok". so the old one'd be deleted and a new one created.

p.s.:
it's very important to install to that directory!
only one thing friend, go to the /usr/lib directory and check if the firefox directory is "mozilla-firefox" or "firefox-mozilla" cause it's important!!!!!!!!!!!!! as soon as you gonna overrite it.
have a nice day.
pavel

---

