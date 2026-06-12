---
title: "Painless laptop upgrade to Hardy!"
date: 2008-04-26
forum: Desktop Environments
---

### Post by dlane on 2008-04-26
Totally trouble free text-based Aptitude upgrade of highly customised (lots of non-standard repositories and software) Gutsy Gibbon install on Asus Z62E (14" Intel Santa Rosa chipset laptop, available from local NZ-based supplier, components to order from [http://insite.co.nz](http://insite.co.nz)).  Only issue was needing to change a file (not sure if it was there beforehand) /var/cache/fontconfig into a dir.  Had to run "dpkg -a reconfigure" as instructed by aptitude, and upgrade finished without issue.  Only had to decided whether or not to keep modified config files. 

With this upgrade, Compiz worked out of the box, multiple monitors (inbuild 1280x800 and external 1680x1050) monitors detected automatically.  Xrandr still allows manual shifts.  Substantially better support for videos and integration with Firefox 3.0b5 for a whole array of plug-ins.  Overall, I'm VERY impressed.  Keep up the good work Ubuntu dev team - I'll be keen to help out, at the very least reporting on getting tricky hardware - like the inbuilt webcam - working.  Haven't test hibernate and suspend yet, but hibernate worked reliably with Gutsy, and Suspend quite well, but occasionally didn't restore wireless after return from Suspend (required reboot). 

Cheers,

Dave

---

