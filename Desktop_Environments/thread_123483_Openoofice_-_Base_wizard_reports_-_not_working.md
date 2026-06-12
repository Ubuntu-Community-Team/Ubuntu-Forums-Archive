---
title: "Openoofice - Base wizard reports - not working"
date: 2006-01-30
forum: Desktop Environments
---

### Post by linuxmad on 2006-01-30
Hi,
I am using oo2 version 2.0.1 in ubuntu breezy and I am not able to create any reports using the wizard. It starts then the status bar on the bottom stops working and there it stays. I tried opening base from the command line and got this output when starting the report's wizard:
ooffice2 -base
java.lang.NullPointerException
at com.sun.star.wizards.ui.TitlesComponent.addTextListener(TitlesComponent.java)
at com.sun.star.wizards.report.ReportWizard.buildSteps(ReportWizard.java)
at com.sun.star.wizards.report.ReportWizard.startReportWizard(ReportWizard.java)
at com.sun.star.wizards.report.CallReportWizard$ReportWizardImplementation.trigger(CallReportWizard.java)

How can I fix this NULLPOINTEREXCEPTION ??????'
Thanks,
José

---

### Post by steve.horsley on 2006-01-30
In my experience, the base wizards are very flakey, although they generally at least try and do something for me. What version of java are you using? Try the command **java -version**. If it's not the Sun version, perhaps you could install that and try again?

---

### Post by linuxmad on 2006-01-30
It's the sun version installed by automatix.
I already reinstalled it and nothing! ... it simply cannot run the wizard...
...But it can run wizards from other apps, like writer and calc... It's very odd...

---

### Post by linuxmad on 2006-01-30
it appears someone reported this already:

Bug#343761: Different exception with 2.0.1-1

Marcus Better
Tue, 03 Jan 2006 03:04:02 -0800

OOo 2.0.1-1 gives the same result but a different NullPointerException:

java.lang.NullPointerException
        at
com.sun.star.wizards.ui.TitlesComponent.addTextListener(TitlesComponent.java)
        at
com.sun.star.wizards.report.ReportWizard.buildSteps(ReportWizard.java)
        at
com.sun.star.wizards.report.ReportWizard.startReportWizard(ReportWizard.java)
        at
com.sun.star.wizards.report.CallReportWizard$ReportWizardImplementation.trigger(CallReportWizard.java)

(This is with Sun JRE 1.5.0 update 05).

---

