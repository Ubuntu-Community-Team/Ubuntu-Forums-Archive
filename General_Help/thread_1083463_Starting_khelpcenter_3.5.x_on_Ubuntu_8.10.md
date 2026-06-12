---
title: "Starting khelpcenter 3.5.x on Ubuntu 8.10"
date: 2009-03-01
forum: General Help
---

### Post by damonrand on 2009-03-01
Hi,

I'm running a fresh standard Ubuntu 8.10 release.

I installed digikam
   sudo apt-get install digikam

and then run digikam and choose handbook and I get
   "could not find service khelpcenter"

So I installed full kde but still the same error. 
   sudo apt-get install kubuntu-desktop

Now apt-get shows khelpcenter is certainly installed. What I see now is that all KDE 3.5.10 apps (Amarok, Digikam, etc) fail to start Help with the same error. 

But all KDE 4.1.14 apps (Kate, Gwenview etc) start Help just fine.

Is this problem related to this issue?
[https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/284915](https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/284915)

Similar bug reports are here but no solution.
[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/307916](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/307916)

Any got help working for Amarok or Digikam?

Regards,
Damon.

---

### Post by gborzi on 2009-03-05
Hello damonrand,
I had the same problem with another kde3 app (kdar, that I packaged myself) and googling around found a fix. There are two problems:
1) kde3 apps don't find the khelpcenter desktop file they need when you open the app's help. This is solved by symlinking the khelpcenter (for kde4) desktop file to the kde3 applications directory, i.e.
> cd /usr/share/applications/kde
sudo ln -s /usr/share/kde4/services/khelpcenter.desktop .
after this your kde3 apps will open the khelpcenter app, that is to say the help window, but it will complain that it has not found the requested item, in your case the digikam entry. This is the second problem.
2)khelpcenter 4 looks in /usr/share/doc/kde4/HTML/en for help files, but kde3 help files are installed in /usr/share/doc/kde/HTML/en, so you need to symlink the corresponding entries, e.g. for kdar I did > cd /usr/share/doc/kde4/HTML/en
sudo ln -s /usr/share/doc/kde/HTML/en/kdar .
for digikam I suppose you need to do the following > cd /usr/share/doc/kde4/HTML/en
sudo ln -s /usr/share/doc/kde/HTML/en/digikam .
In these examples I assumed you are using english as default language, if you are using another language change "en" accordingly, for example for italian > cd /usr/share/doc/kde4/HTML/it
sudo ln -s /usr/share/doc/kde/HTML/it/digikam .

Hope this helps.

---

### Post by izak on 2009-03-25
Thanks a lot! That helped me to access Kile's help.  :)

---

