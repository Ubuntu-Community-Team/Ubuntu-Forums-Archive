---
title: "hpijs and HP OfficeJet Pro K8600"
date: 2009-01-04
forum: General Help
---

### Post by Ole Juul on 2009-01-04
After years of using Linux I've still never been able to print properly. I would be grateful if someone could help me realize my dream of a fully functional Linux system.

Last year I purchased an HP OfficeJet Pro K8600 and have found that Kubuntu 6.04 has a driver which is close and offers partial functionality, but I still have to ask a friend with a MicroSoft OS to help me whenever I want to fully use it.

I would like, however, to use the printer with Kubuntu 8.04 but the same driver does not seem to be available there. I've installed the HP libraries but the Kubuntu printer installer only shows a few OfficeJet models and they are different ones from the ones in 6.04 so I can't use the printer at all there. Also the "scan" facility does nothing, but when I manually enter the printer URL the wizard will give the little printer list. I am able to ping the printer.

The Linux Foundation Open Printing database shows this model as working "perfectly". Is there a way that I can realize their vision and perhaps duplicate their experience, so that I too may print using an HP K8600?

---

### Post by sigurnjak on 2009-01-05
You can try this: 
[http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777&release_id=647853](http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777&release_id=647853)

It is newer then one in the repo

---

### Post by Ole Juul on 2009-01-05
That did the trick!
Many, many, thanks sigurnjak! After years of not having a printer in Linux I now have one for the first time. So, the trick is to ignore the system setup GUI.

Installing HPLIP (which includes HPIJS) is easy using the HP automatic installer. I just did it on two machines (Kubuntu 6.04 and 8.04) and there were a couple of errors but running the script again fixed that. The instructions for doing it all by hand don't look that daunting either. The home of Hewlett-Packard's Linux Imaging and Printing software can be found at: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

All my grief (and probably many other people's) could have been avoided by providing a window in the "system setup" with simple instructions about where to get drivers, instead of a GUI WIZARD of limited functionality. (sigh)

---

### Post by sigurnjak on 2009-01-05
You are welcome friend , just go easy on the ink  , it is expensive !:D

---

