---
title: "Kontact / Korganizer crash on startup"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Plutarch on 2008-05-08
Whenever I try to start up Kontact or Korganizer, the program crashes immediately.

I think the problem is due to a bug related to the the fact that I added an attachment to a Calender event, since it first crashed after I added the attachment, and I have heard rumors of such a bug existing. As well, other Kontact programs (e.g. KMail) work properly.

Is there any way to delete the attachment (I think this might fix the problem) without opening Kontact / Korganizer.

Thanks very much for any suggestions

P.S. Here is what it tells me when it crashes:

The application Kontact crashed and caused the signal 11 (SIGSEGV)

Backtrace:
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb5f2c920 (LWP 9177)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb5feb283 in strlen () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6b0379c in QString::fromUtf8 () from /usr/lib/libqt-mt.so.3
#8  0xb7d90b31 in KCal::Attachment::Attachment () from /usr/lib/libkcal.so.2
#9  0xb7db9670 in KCal::ICalFormatImpl::readAttachment ()
   from /usr/lib/libkcal.so.2
#10 0xb7dbfb03 in KCal::ICalFormatImpl::readIncidence ()
   from /usr/lib/libkcal.so.2
#11 0xb7dbfe1b in KCal::ICalFormatImpl::readEvent ()
   from /usr/lib/libkcal.so.2
#12 0xb7dc0c06 in KCal::ICalFormatImpl::populate () from /usr/lib/libkcal.so.2
#13 0xb7db5cfa in KCal::ICalFormat::fromRawString ()
   from /usr/lib/libkcal.so.2
#14 0xb7db6337 in KCal::ICalFormat::load () from /usr/lib/libkcal.so.2
#15 0xb7de0bf6 in KCal::FileStorage::load () from /usr/lib/libkcal.so.2
#16 0xb7da7ff4 in KCal::CalendarLocal::load () from /usr/lib/libkcal.so.2
#17 0xb7de449d in KCal::ResourceLocal::doLoad () from /usr/lib/libkcal.so.2
#18 0xb7de358b in KCal::ResourceCalendar::load () from /usr/lib/libkcal.so.2
#19 0xb7df1e7e in KCal::CalendarResources::load () from /usr/lib/libkcal.so.2
#20 0xb4adbad5 in KOrganizerPart::KOrganizerPart ()
   from /usr/lib/kde3/libkorganizerpart.so
#21 0xb4adc86d in KParts::GenericFactory<KOrganizerPart>::createPartObject ()
   from /usr/lib/kde3/libkorganizerpart.so
#22 0xb767e25f in KParts::Factory::createPart () from /usr/lib/libkparts.so.2
#23 0xb7e5bf06 in Kontact::Core::createPart ()
   from /usr/lib/libkpinterfaces.so.1
#24 0xb7e5d767 in Kontact::Plugin::loadPart ()
   from /usr/lib/libkpinterfaces.so.1
#25 0xb594fed5 in KOrganizerPlugin::createPart ()
   from /usr/lib/kde3/libkontact_korganizerplugin.so
#26 0xb7e5d6d3 in Kontact::Plugin::part () from /usr/lib/libkpinterfaces.so.1
#27 0x08062a50 in ?? ()
#28 0x08224bb0 in ?? ()
#29 0x00000000 in ?? ()

---

### Post by lesergi on 2008-05-08
Hi!

Can you paste here the konsole exit?

Bye!

---

### Post by p_quarles on 2008-05-08
The files to look at are the ones inside:
```
~/.kde/share/apps/korganizer/
```
as well as:
```
~/.kde/share/config/korganizerrc
```
You should be able to find and eliminate the troublesome file in one of those places.

---

### Post by Plutarch on 2008-05-08
Thanks for the help everyone.
I found a fix.
Move the file 
home/.kde/share/apps/korganizer/std.ics to another folder.
Open kontact (it won't crash with this folder removed).
Add back the file to its original folder.
Delete the attachement using kontact.

Fixed!

---

