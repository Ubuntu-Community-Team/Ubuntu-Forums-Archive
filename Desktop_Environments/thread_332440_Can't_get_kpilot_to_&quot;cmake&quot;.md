---
title: "Can't get kpilot to &quot;cmake&quot;"
date: 2007-01-06
forum: Desktop Environments
---

### Post by eg-maverick on 2007-01-06
I've been trying to find a sync solution for my palm powered phone (no- I won't use Evolution or it's sync stuff - too many problems). I like the PIM interface available with Kontact and read about Kpilot. I tried compiling from the source according to the kpilot website, [http://cvs.codeyard.net/kpilot/develop.php](http://cvs.codeyard.net/kpilot/develop.php) but run into massive make errors. I have loaded all the libraries and options it discusses but can't figure out what to do next. Here is the log: Can anyone help?

root@forbescw-laptop:~/kpilot# make -f Makefile.cmake
test -d "build-Linux2_6_17_10_386" || mkdir -p "build-Linux2_6_17_10_386"
test -d "build-Linux2_6_17_10_386"
SRC_DIR=`pwd` ; cd "build-Linux2_6_17_10_386" && cmake $SRC_DIR
-- Found KDE3 include dir: /usr/include/kde
-- Found KDE3 library dir: /usr/lib
-- Found KDE3 dcopidl preprocessor: /usr/bin/dcopidl
-- Found KDE3 dcopidl2cpp preprocessor: /usr/bin/dcopidl2cpp
-- Found KDE3 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found pi-dlp.h in /usr/include
-- Found libpisock in /usr/lib/libpisock.so
-- Found pilot-link: /usr/lib/libpisock.so
-- Could not find libmal.h
-- Could not find libmal
-- Couldn't find mal. Won't be able to build malconduit
-- icon: /root/kpilot/kpilot/Icons/mini-kpilot.png doesn't fit naming conventions. ignoring.
-- icon: /root/kpilot/kpilot/Icons/fastsync.png doesn't fit naming conventions. ignoring.
-- icon: /root/kpilot/kpilot/Icons/nosync.png doesn't fit naming conventions. ignoring.
-- icon: /root/kpilot/kpilot/Icons/busysync.png doesn't fit naming conventions. ignoring.
-- icon: /root/kpilot/kpilot/Icons/hotsync.png doesn't fit naming conventions. ignoring.
-- icon: /root/kpilot/kpilot/Icons/kpilot- splash.png doesn't fit naming conventions. ignoring.
-- Couldn't find mal. Won't be able to build malconduit
-- BUILD: Normal build selected.
-- Configuring done
-- Generating done
-- Build files have been written to: /root/kpilot/build-Linux2_6_17_10_386
make[1]: Entering directory `/root/kpilot/build-Linux2_6_17_10_386'
make[2]: Entering directory `/root/kpilot/build-Linux2_6_17_10_386'
[  5%] Built target kpilot
[ 22%] Built target kcm_kpilot
[ 32%] Built target kpilotDaemon
[ 37%] Built target kpilotTest
[ 54%] Built target kpilot_bin
[ 59%] Built target conduit_address
[ 67%] Built target conduit_doc
[ 71%] Built target kpalmdoc
[ 74%] Built target conduit_memofile
[ 77%] Built target conduit_notepad
[ 79%] Built target conduit_null
[ 82%] Built target conduit_popmail
[ 85%] Built target conduit_sysinfo
[ 88%] Built target conduit_time
make[3]: Entering directory `/root/kpilot/build-Linux2_6_17_10_386'
[ 88%] Building CXX object conduits/vcalconduit/CMakeFiles/conduit_todo.dir/vcal-conduitbase.o
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:42:30: error: libkcal/calendar.h: No such file or directory
/root/kpilot/conduits/vcalconduit/vcal- conduitbase.cc:43:35: error: libkcal/calendarlocal.h: No such file or directory
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:44:39: error: libkcal/calendarresources.h: No such file or directory
In file included from /root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/vcal- conduitbase.moc:11,
                 from /root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:51:
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal-conduitbase.h:35:35: error: libkcal/calendarlocal.h: No such file or directory
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:55:2: warning: #warning "Using an old version of libkcal with timezone bug."
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:356:2: warning: #warning "Timezone bug is present."
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In destructor 'virtual VCalConduitBase::~VCalConduitBase()':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:85: warning: possible problem detected in invocation of delete operator:
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:85: warning: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:42: warning: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:85: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual bool VCalConduitBase::exec()':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:185: warning: possible problem detected in invocation of delete operator:
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:185: warning: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:42: warning: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:185: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual bool VCalConduitBase::openCalendar()':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:255: error: 'CalendarResources' is not a member of 'KCal'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:255: error: 'rescal' was not declared in this scope
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:278: error: expected type-specifier
/root/kpilot/conduits/vcalconduit/vcal- conduitbase.cc:278: error: cannot convert 'int*' to 'KCal::Calendar*' in assignment
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:278: error: expected `;'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc :288: error: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal-conduitbase.h:42: error: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:290: error: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:42: error: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:292: error: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:42: error: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:310: error: expected type-specifier
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc :310: error: expected `>'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:310: error: expected `('
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:310: error: 'CalendarLocal' is not a member of 'KCal'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:310: error: expected primary-expression before '>' token
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:310: error: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal-conduitbase.h:42: error: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc :311: error: expected `)' before '{' token
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:340: error: expected type-specifier
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:340: error: expected `;'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:359: error: invalid use of undefined type 'struct KCal::Calendar'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:42: error: forward declaration of 'struct KCal::Calendar'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual int VCalConduitBase::resolveConflict(KCal::Incidence*, PilotRecordBase*)':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:431: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual KCal::Incidence* VCalConduitBase::changeRecord(PilotRecord*, PilotRecord*)':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:459: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:459: error: incomplete type 'KCal::Incidence' used in nested name specifier
/root/kpilot/conduits/vcalconduit/vcal- conduitbase.cc:472: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal-conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:472: error: incomplete type 'KCal::Incidence' used in nested name specifier
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual void VCalConduitBase::deletePalmRecord(KCal::Incidence*, PilotRecord*)':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:533: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc: In member function 'virtual void VCalConduitBase::updateIncidenceOnPalm(KCal::Incidence*, PilotRecordBase*)':
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:551: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:551: error: incomplete type 'KCal::Incidence' used in nested name specifier
/root/kpilot/conduits/vcalconduit/vcal- conduitbase.cc:554: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal-conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:568: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:569: error: invalid use of undefined type 'struct KCal::Incidence'
/root/kpilot/build-Linux2_6_17_10_386/conduits/vcalconduit/../../../conduits/vcalconduit/vcal- conduitbase.h:43: error: forward declaration of 'struct KCal::Incidence'
/root/kpilot/conduits/vcalconduit/vcal-conduitbase.cc:569: error: incomplete type 'KCal::Incidence' used in nested name specifier
make[3]: *** [conduits/vcalconduit/CMakeFiles/conduit_todo.dir/vcal- conduitbase.o] Error 1
make[3]: Leaving directory `/root/kpilot/build-Linux2_6_17_10_386'
make[2]: *** [conduits/vcalconduit/CMakeFiles/conduit_todo.dir/all] Error 2
make[2]: Leaving directory `/root/kpilot/build-Linux2_6_17_10_386'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/kpilot/build-Linux2_6_17_10_386'
make: *** [all] Error 2
root@forbescw-laptop:~/kpilot#

---

### Post by tomchuk on 2007-01-06
looks like your missing the kcal headers `apt-get install libkcal2-dev` should do the trick.

---

### Post by eg-maverick on 2007-01-06
Thanks. That seemed to do it. I got a bunch of "warnings" but no errors.
Thanks again.
Craig

---

