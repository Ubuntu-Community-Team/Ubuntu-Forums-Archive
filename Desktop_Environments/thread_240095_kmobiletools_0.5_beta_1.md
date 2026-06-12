---
title: "kmobiletools 0.5 beta 1"
date: 2006-08-20
forum: Desktop Environments
---

### Post by bryanchapman9999 on 2006-08-20
Hi,

Anyone complied this from source?

I'm getting the folowing on dapper...

bryan@amber:~/kmobil_build$ make
Makefile:854: warning: overriding commands for target `clean-bcheck'
Makefile:817: warning: ignoring old commands for target `clean-bcheck'
Makefile:859: warning: overriding commands for target `bcheck-am'
Makefile:822: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/home/bryan/kmobil_build'
Makefile:854: warning: overriding commands for target `clean-bcheck'
Makefile:817: warning: ignoring old commands for target `clean-bcheck'
Makefile:859: warning: overriding commands for target `bcheck-am'
Makefile:822: warning: ignoring old commands for target `bcheck-am'
Making all in kmobiletools
make[2]: Entering directory `/home/bryan/kmobil_build/kmobiletools'
/bin/sh ../libtool --silent --tag=CXX --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o kmobiletools -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib    main.o kmobiletools.o c_config.o device.o ui_sDevice.o mainWidget.o d_pickphonebook.o ui_PickPhonebook.o ui_sPhone.o c_sms.o ui_SMSList.o d_smslist.o ui_NewSMS.o d_newsms.o threadedgsm.o gsm.o ui_sPhoneBook.o c_smslist.o ui_sSMS.o d_settingsui.o d_terminal.o gsmdatacontainer.o dcopinterface_skel.o mainWidget.moc.o ui_SMSList.moc.o ui_NewSMS.moc.o ui_sPhone.moc.o ui_sSMS.moc.o ui_sPhoneBook.moc.o ui_PickPhonebook.moc.o ui_sDevice.moc.o  -lkabc_file -lkdecore -lkio -lkabc -lkdeui -lkhtml 
: command not found.la: line 6: 
: command not found.la: line 9: 
: command not found.la: line 12: 
: command not found.la: line 15: 
: command not found.la: line 18: 
: command not found.la: line 23: 
: command not found.la: line 26: 
: command not found.la: line 29: 
: command not found.la: line 33: 
: No such file or directoryder.dll.a
make[2]: *** [kmobiletools] Error 1
make[2]: Leaving directory `/home/bryan/kmobil_build/kmobiletools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/kmobil_build'
make: *** [all] Error 2
bryan@amber:~/kmobil_build$ 


Thanks for any help
bryan

---

