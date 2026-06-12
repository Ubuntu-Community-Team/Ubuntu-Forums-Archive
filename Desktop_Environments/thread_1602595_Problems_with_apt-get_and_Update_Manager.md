---
title: "Problems with apt-get and Update Manager"
date: 2010-10-21
forum: Desktop Environments
---

### Post by SavannahSoftware on 2010-10-21
Installed 10.10 the other day. Ever since then, I find apt-get in the System Monitor using high CPU levels. I have to kill the process.

I'm not sure if these are connected, but every time I manually do a "Check for Updates", it asks me for the original install disk.

I just did a manual update, and it ended with the following:


> ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for menu ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up alsa-utils (1.0.23-2ubuntu3.3) ...
dpkg: error processing alsa-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-cupshelpers (1.2.3+20100723-0ubuntu8.1) ...
No apport report written because MaxReports is reached already
Setting up python-papyon (0.5.1-0ubuntu2) ...
Setting up system-config-printer-common (1.2.3+20100723-0ubuntu8.1) ...
Setting up system-config-printer-gnome (1.2.3+20100723-0ubuntu8.1) ...
Setting up system-config-printer-udev (1.2.3+20100723-0ubuntu8.1) ...
Setting up tomboy (1.4.0-0ubuntu3) ...
Processing triggers for python-support ...
Processing triggers for menu ...
Errors were encountered while processing:
 alsa-utils
Setting up alsa-utils (1.0.23-2ubuntu3.3) ...
dpkg: error processing alsa-utils (--configure):
 subprocess installed post-installation script returned error exit status 1


Any help would be appreciated.

---

### Post by gobbles414 on 2010-10-21
Based on the [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/664645](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/664645) bug report, I suspect that a fix for this issue will become available very soon.

Consider doing a "complete removal" of the alsa-utils and unbuntu-desktop packages. You can then reinstall those packages once the bug in question has been fixed.

---

### Post by SavannahSoftware on 2010-10-21
Thanks for the reply. Do you think this has anything to do with my other two issues (repeatedly asking for the install CD, and apt-get hanging with high CPU usage?

---

### Post by gobbles414 on 2010-10-21
The high CPU usage and asking for the CD might be related to one another. Please go System => Administration => Synaptic Package Manager => Settings => Repositories. This will display the "Software Sources" window, Are there any checkmarks in the "Installable from CD-ROM/DVD" category. If yes, remove the checkmarks => close the Software Sources window => then click on "Reload" in the  upper-left of the Synaptic window.

Regarding the alsa-utils problem... I was able to solve the problem on my computer by doing a complete removal of alsa-utils and ubuntu-desktop, then selecting ubuntu-desktop for installation, then doing a "Force Version" install of an older version of alsa-utils (highlight the package then go Package => Force Version), then applying the installation. Do not update from the older alsa-package until apt and/or Update Manager reports a version newer than 1.0.23-2ubuntu3.3.

---

### Post by SavannahSoftware on 2010-10-21
Great. Thanks for that. I did have the check-mark to install from CD. I'm sure that will stop it now.

Regarding the apt-get hanging, I think I'll just wait to see if it's cured with an update soon. If not, I'll try the reinstall route.

I appreciate your help.

---

### Post by SantaFe on 2010-10-21
Just checked with update manager & got a new alsa-utils 1.0.23-2ubuntu3.4.  Confirmed it's working now, because when I went to install sysinfo before, I got that error message, now when I tried it, error-less! ;)

---

### Post by SavannahSoftware on 2010-10-21
Great. Just got it too. Gotta love Ubuntu. :-)

---

### Post by gobbles414 on 2010-10-23
The new alas-utils update installed well for me too.

Please note that both the broken version of the update and the fixed version are considered "proposed" updates (experimental updates submitted to Ubuntu users for testing). There is a checkbox to turn that option on/off in Administration => Synaptic Package Manager => Settings => Repositories => Updates. It is supposed to be off by default, but it might have gotten activated if you upgraded to Ubuntu 10.10 from an older version of Ubuntu versus a "fresh install", installed a beta version of 10.10, etc.

I do NOT recommend disabling proposed updates if you have already downloaded updates from there (which you have), because doing so could cause difficulties in installing updates in the future (because version numbers won't be as expected). If you feel that you must disable proposed updates, visit [http://ubuntuforums.org/showthread.php?t=432636](http://ubuntuforums.org/showthread.php?t=432636) for instructions on how to revert all proposed updates to stable ones. I've never reverted using that method, but my guess is you should substitute maverick for feisty in the command line input.

---

### Post by tgbrooks on 2010-10-24
I have the same problem as the original poster had: I upgraded my 10.04 to a 10.10 install and since then apt-get starts up every time and chews up an entire core on my CPU. I've got the latest alsa-utils (1.0.23-2ubuntu3), though, and still have the same problem. Any suggestions?

I also had the update manager requesting the CD to install error.

---

### Post by gobbles414 on 2010-10-26
tgbrooks, here are a few possibilities for your consideration (in no particular order):

1. Have you removed all checkmarks from the CD-ROM/DVD category in Software Sources? It may help to restart your computer after making that change.

2. Although many people in these forums say otherwise, it has been my experience the upgrading without reformatting isn't effective on any operating system (Ubuntu, Mac OS X, Windows, etc). I recommend a "fresh install"

3. The alsa-utils (1.0.23-2ubuntu3) package is the latest "stable" version, but there is a newer version available in "proposed updates" You may wish to enable that (see previous posts in this thread), and then look in the Update Manager to see if any of those are updates to apt, Update Manager, etc. If you don't see anything of interest, or don't feel that installing proposed updates is worth the risk, you can disable proposed updates without installing any of the packages. As I mentioned in an earlier post, it is extremely difficult to revert to stable after installing packages from proposed updates; choose carefully...

4. You may wish to run some software maintenance. I recommend that you install a program called bleachbit (available in apt, Synaptic, etc). After installation, go to System Tools and run both normal and "as root" versions of the bleachbit. Be careful to read all warnings, so you don't delete bookmarks, etc. You may also wish to manually run something known as "crons" (along with a couple of other helpful procedures). Open a terminal, and enter the following... Again, restarting your computer after all of that is complete may be helpful.

sudo apt-get --purge autoremove && sudo apt-get --purge autoclean && sudo run-parts -v /etc/cron.hourly && sudo run-parts -v /etc/cron.weekly && sudo run-parts -v /etc/cron.monthly && sudo run-parts -v /etc/cron.daily

Please, keep us up-to-date on your progress.

---

### Post by tgbrooks on 2010-10-31
Thanks for the suggestions gobbles. However, the problem has gone away. I can't remember changing anything, so this is a little odd. Oh well.

---

### Post by gobbles414 on 2010-11-06
Perhaps the problem solved itself as the result of a recent update?

---

