---
title: "problem with open office 3.1 database"
date: 2009-05-09
forum: General Help
---

### Post by Mickser_52 on 2009-05-09
I have recently updated to Jaunty jackalope and so far no major problems. I have just downloaded Open Office 3.1 through Synaptic package manager and find that when I click on the database from Applications menu The Open Office startup screen appears and then nothing further happens. If I open the word processor and try to open the database application from there I get an error message saying that open office has crashed due to an unexpected problem.

Has anyone else had this problem and perhaps have a solution.

---

### Post by jazzman65 on 2009-05-09
I've had the same problem with OpenOffice Database 3.1, but the other applications start up and run fine.  Unfortunately, I've not found a solution for the database's failure to start up.  :(

---

### Post by lyni on 2009-05-10
I thought that OpenOffice 3 was already installed with Ubuntu 9.04 so you didn't have to separately install it. but perhaps if you go to the openoffice forums they might be able to help with your problem. the link is in my signature.

---

### Post by yankeeDDL on 2009-05-10
Till yesterday the repositories for OO3.1 were still building. There are other threads on this.
You probably have installed only part of OO3.1
If you need to use OO urgently, I suggest you revert back to 3.0 and wait a few more days before moving to 3.1.

If you must use 3.1, then you may be better off downloading the .deb file, however, I  would suggest you just add the repositories and deal with the update via the Update-manager.

---

### Post by jazzman65 on 2009-05-11
Sounds good YankeeDDL, that's kind of what I figured might be going on.

---

### Post by leonardo_neo on 2009-05-13
I too have similar problem after I installed OO 3.1 yesterday. I haven't find any solution yet.

---

### Post by Docaltmed on 2009-05-13
It's not just a Jaunty problem. I'm having a similar issue on Intrepid, and I saw another report of the same bug on launchpad. Curiously, no reports that I saw over on the openoffice forums.

I can't get Base to run. Not from Quicklaunch, not from command line, not from another OO component. It just. won't. start.

---

### Post by Hagar Delest on 2009-05-13
Try the official version from Sun: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) And/or [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process, configuration files from the former version might corrupt the new profile.

---

### Post by Mickser_52 on 2009-05-15
Hagar I tried your suggestion. Unfortunately it has made no difference. The database still won't open. I now have a new user folder but did not see any Welcome process that was referred to in your links?

Also when I click on report a problem in the office help menu nothing happens.

Presumably the problem will be sorted eventually.

---

### Post by twlite-phoenix on 2009-05-15
Try:  sudo apt-get install openoffice.org-evolution

Credit: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) (Comment #11)

---

### Post by Mickser_52 on 2009-05-15
Thanks Twlite-phoenix, database is opening now:D

---

### Post by Hagar Delest on 2009-05-15
> **Mickser_52 said:**
> I now have a new user folder but did not see any Welcome process that was referred to in your links?
Then it means that the user profile has not been reset. Are you sure you've renamed the right one? The .../user/3/ one, not the openoffice.org2/user one.

---

### Post by Mickser_52 on 2009-05-16
Hagar, Yes I am sure. I opened the .openoffice.org folder, there was only one folder there labelled 3. I renamed user to user.old, restarted openoffice and it opened as it had previously.. no welcome message! When I looked in openoffice.org/3 again there were two file, the user.old file and a new user file.

The problem has been solved by Twlite-phoenix suggestion i.e.

sudo apt-get install openoffice.org-evolution
 
Thanks for your response

---

### Post by simonthd on 2009-05-16
Thanks twlite ! I works fine now.

---

### Post by DeMus on 2009-05-16
> **twlite-phoenix said:**
> Try:  sudo apt-get install openoffice.org-evolution

Credit: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) (Comment #11)

It works!!! But what does Evolution have to do with Openoffice?

---

### Post by Hagar Delest on 2009-05-16
That's the problem with the dependencies of versions repackaged by a distro. It may install some files needed by Base, that are not installed if that package is missing.

I'm still surprised by the fact that the Ubuntu version of OOo doesn't prompt for the welcome process when there is no profile!

---

