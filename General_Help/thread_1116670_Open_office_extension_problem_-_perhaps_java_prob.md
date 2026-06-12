---
title: "Open office extension problem - perhaps java prob?"
date: 2009-04-05
forum: General Help
---

### Post by Glen Darby on 2009-04-05
Hi,

I've been running open office 2.4 successfully on one of my computers running Ubuntu 8.4 and in the Ooo database I have the menu extension and report builder running ok.

On a new build computer I have installed ubuntu 8.10, open office 2.4 and in the Ooo database I have the menu extension running fine, but I had one heck of a job installing the report builder which would not install directly from the download link and I eventually installed it by going sudo nautilus and installing with the package installer in Base, but although it runs and opens a new report sheet for me, it will not actually run any of the reports that I have transfered accross or any new report I make...

Warning is : An exception of type com.sun.star.uno.RuntimeException was caught.

Error is : > [jni_uno bridge error] UNO calling Java method execute: non-UNO exception occurred: java.lang.NoClassDefFoundError: org/jfree/report/JFreeReportBoot

java stack trace:

java.lang.NoClassDefFoundError: org/jfree/report/JFreeReportBoot

	at com.sun.star.report.pentaho.PentahoReportEngine.<init>(PentahoReportEngine.java:54)

	at com.sun.star.report.pentaho.SOReportJobFactory$_SOReportJobFactory.execute(SOReportJobFactory.java:219)


I've checked the java thats running and it is version 1.6.0_0
I'm sure it should be version 1.6.0_07 which is what is on my other machine but I can't seem to get hold of a download of that version and I don't understand why it wasn't included with Ubuntu or Open office.

Does anyone have any ideas please..

Glen.

---

