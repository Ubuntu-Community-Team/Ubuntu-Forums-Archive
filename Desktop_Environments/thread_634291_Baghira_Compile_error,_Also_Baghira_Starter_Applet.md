---
title: "Baghira Compile error, Also Baghira Starter Applet Error"
date: 2007-12-07
forum: Desktop Environments
---

### Post by menacers on 2007-12-07
i have read other posted and followed them carefully but i am still experiencing a few problems.

I can't compile the latest baghira on my Kubuntu.  here is the last few lines of my MAKE command:


baghiraclient.moc:344: error: 'KDecoration' has not been declared
baghiraclient.moc: In member function 'virtual bool Baghira::BaghiraClient::qt_property(int, int, QVariant*)':
baghiraclient.moc:352: error: 'KDecoration' has not been declared
baghiraclient.cc: In member function 'virtual bool Baghira::BaghiraFactory::reset(long unsigned int)':
baghiraclient.cc:362: warning: control reaches end of non-void function
make[3]: *** [baghiraclient.lo] Error 1
make[3]: Leaving directory `/home/user/Desktop/baghira-0.8/deco'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/user/Desktop/baghira-0.8/deco'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/baghira-0.8'
make: *** [all] Error 2



As a workaround i downloaded 45615-kwin-baghira_0.8-1_i386 from the repos and that worked fine.  but now when i try to load the baghira starter applet ot menubar i get the follwing error:

The Baghira Starter applet could not be loaded. Please check your installation.


please help!!!!


Arif
kubuntu on t40 thinkpad

---

