---
title: "Evolution Calendar + Exchange = Crash"
date: 2008-05-20
forum: Desktop Environments
---

### Post by jtuchscherer on 2008-05-20
Hi there,

Since I updated to Hardy I have a lot of problems accessing my work calendar (MS Exchange 2003). In most cases it gives me an error message right away when I look at the calendar ('An unexpected error happened. Calendar won't work until the next restart of evolution.'). Sometimes I can look at the calendar for a few seconds before I get the error message.
Overall the exchange support in evolution seems to be more unstable now. I need to restart it a lot because it lost the connection to the backend process.

Did somebody else experience similar problems with evolution in hardy and exchange? I wanted to check the feedback here first before I file a ticket in launchpad. Maybe there is an easy workaround.

Thanks in advance,
Johannes

---

### Post by pete on 2008-05-27
I've been seeing exactly the same behavior, and it's causing me no end of frustration.  Everything worked fine following my initial upgrade to Hardy, but then I started getting this same error a week or two later, following some Evolution updates.

dmesg shows a segfault in the evolution-exchange process, but no amount of googling/searching/reinstalling/etc has resolved it for me.

Wish I had better news, but it's made Evolution pretty much unusable for me.

---

### Post by holodad on 2008-05-28
Hello

I'am having the same issue but for me, since i upgraded to Hardy, i was never able to launch correctly evolution with exchange connector.
It crashes imediately after typing toto@silver:# evolution. If i launch evolution without any plugins, it starts... 
Here is the error message that i get:

077000-b6078000 rw-p 00005000 08:06 364659     /usr/lib/evolution/2.22/libefilterbar.so.0.0.0
b6078000-b607d000 r-xp 00000000 08:06 364672     /usr/lib/evolution/2.22/libevolution-calendar-importers.so.0.0.0
b607d000-b607e000 rw-p 00004000 08:06 364672     /usr/lib/evolution/2.22/libevolution-calendar-importers.so.0.0.0
b607e000-b6080000 r-xp 00000000 08:06 364655     /usr/lib/evolution/2.22/libeabutil.so.0.0.0
b6080000-b6081000 rw-p 00002000 08:06 364655     /usr/lib/evolution/2.22/libeabutil.so.0.0.0
b6081000-b608f000 r-xp 00000000 08:06 364677     /usr/lib/evolution/2.22/libmenus.so.0.0.0
b608f000-b6090000 rw-p 0000e000 08:06 364677     /usr/lib/evolution/2.22/libmenus.so.0.0.0
b6090000-b60c3000 r-xp 00000000 08:06 224716     /usr/lib/libsoup-2.4.so.1.1.0
b60c3000-b60c5000 rw-p 00032000 08:06 224716     /usr/lib/libsoup-2.4.so.1.1.0
b60c5000-b6103000 r-xp 00000000 08:06 222744     /usr/lib/libexchange-storage-1.2.so.3.0.0
b6103000-b6105000 rw-p 0003e000 08:06 222744     /usr/lib/libexchange-storage-1.2.so.3.0.0
b6105000-b6108000 r-xp 00000000 08:06 364756     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-google.so
b6108000-b6109000 rw-p 00002000 08:06 364756     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-google.so
b6109000-b610e000 r-xp 00000000 08:06 364746     /usr/lib/evolution/2.22/plugins/liborg-gnome-gw-account-setup.so
b610e000-b610f000 rw-p 00004000 08:06 364746     /usr/lib/evolution/2.22/plugins/liborg-gnome-gw-account-setup.so
b610f000-b6111000 r-xp 00000000 08:06 368171     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-caldav.so
b6111000-b6112000 rw-p 00002000 08:06 368171     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-caldav.so
b6112000-b6115000 r-xp 00000000 08:06 364749     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-hula-account-setup.so
b6115000-b6116000 rw-p 00002000 08:06 364749     /usr/lib/evolution/2.22/plugins/liborg-gnome-evolution-hula-account-setup.so
b6116000-b6152000 r-xp 00000000 08:06 364678     /usr/lib/evolution/2.22/components/libevolution-addressbook.so
b6152000-b6155000 rw-p 0003c000 08:06 364678     /usr/lib/evolution/2.22/components/libevolution-addressbook.so
b6155000-b621e000 r-xp 00000000 08:06 364680     /usr/lib/evolution/2.22/components/libevolution-mail.so
b621e000-b6227000 rw-p 000c8000 08:06 364680     /usr/lib/evolution/2.22/components/libevolution-mail.so
b6227000-b6331000 r-xp 00000000 08:06 364679     /usr/lib/evolution/2.22/components/libevolution-calendar.so
b6331000-b6338000 rw-p 0010a000 08:06 364679     /usr/lib/evolution/2.22/components/libevolution-calendar.so
b6338000-b6339000 rw-p b6338000 00:00 0 
b6339000-b6357000 r-xp 00000000 08:06 368177     /usr/lib/evolution/2.22/plugins/liborg-gnome-exchange-operations.so
b6357000-b6358000 rw-p 0001e000 08:06 368177     /usr/lib/evolution/2.22/plugins/liborg-gnome-exchange-operations.so
b6358000-b63bc000 r--p 00000000 08:06 253491     /usr/share/locale-langpack/fr/LC_MESSAGES/evolution-2.22.mo
b63bc000-b63c2000 r-xp 00000000 08:06 287939     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b63c2000-b63c3000 rw-p 00005000 08:06 287939     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b63c3000-b63ce000 r-xp 00000000 08:06 287889     /usr/lib/gtk-2.0/2.10.0/engines/libthinice.so
b63ce000-b63cf000 rw-p 0000a000 08:06 287889     /usr/lib/gtk-2.0/2.10.0/engines/libthinice.so
b63cf000-b63d9000 r--p 00000000 08:06 253482     /usr/share/locale-langpack/fr/LC_MESSAGES/glib20.mo
b63d9000-b63fb000 r--p 00000000 08:06 251705     /usr/share/locale-langpack/fr/LC_MESSAGES/libc.mo
b63fb000-b63fe000 r--p 000000Abandon


Have anybody else getting this issue? For me, it's impossible to use the latest evo with Exch connector...

Thanks a lot for your feedback

Cheers

---

### Post by commonlyUNIQU3 on 2008-06-04
> **jtuchscherer said:**
> Hi there,

Since I updated to Hardy I have a lot of problems accessing my work calendar (MS Exchange 2003). In most cases it gives me an error message right away when I look at the calendar ('An unexpected error happened. Calendar won't work until the next restart of evolution.'). Sometimes I can look at the calendar for a few seconds before I get the error message.
Overall the exchange support in evolution seems to be more unstable now. I need to restart it a lot because it lost the connection to the backend process.

Did somebody else experience similar problems with evolution in hardy and exchange? I wanted to check the feedback here first before I file a ticket in launchpad. Maybe there is an easy workaround.

Thanks in advance,
Johannes

Same frustrating experience for me as well.  I've been using Evolution for work (MS Exchange 2003) for 9 months with not as many issues as I've had in the last week.

---

### Post by posburn on 2008-06-16
No good news to report here; I'm having a similar problem.  All was okay when I first upgraded to Hardy, but now Evolution crashes if I try to compose messages or access my Calendar.  Oddly, I can still receive email okay.  Hope this gets addressed with an update soon - it's unusable as is.

OP, did you file a bug report?

---

### Post by jtuchscherer on 2008-06-18
> **posburn said:**
> OP, did you file a bug report?

There was already one. You can see it here:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/191548]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/191548")

I just saw that I got an answer. So I am going to provide the info  that is asked for. 
After all evolution is now a bit more stable. It doesn't crash on me all the time anymore. Before the recent updates it always crashed, now it only crashes occasionally.

---

### Post by posburn on 2008-06-18
I'm glad the recent updates seemed to have improved things for you.  For me, things got much, much worse.  Now, evolution takes about five minutes to start (from GUI or terminal) and *still* crashes if I try to compose email or check the calendar.  :confused:

---

### Post by stand on 2009-04-28
I don't know if this is the same problem as others have had but I had some problems with my exchange calendar not loading into evolution and crashing. 

A solution that worked for me was to remove the cache.ics calendar file in my ~/.evolution/exchange/<account>/personal/subfolders/Calendar directory. When I restarted evolution, I was able to load the calendar again. 

Presumably, there was some corruption in that cache.ics file that evolution choked on. After my restart the cache.ics file was rewritten to that directory and everything seems to work for now.

BTW this is the Jaunty release.

---

### Post by combatkenpo66 on 2010-02-15
Is anyone else seeing this issue again?  I've been working fine on 9.10 with Evol, but in the last two weeks I've lost my calendar.  Mail works fine, but every time I try to bring up the calendar I get "The Evolution calendars have quit unexpectedly" and it also kills the backend mail process.

I've tried deleting the cache.ics, created a new email account, nothing seems to be working.

---

### Post by louderms on 2010-03-02
I echo everyone elses woes with evolution.  It seemed to work a little better before I upgraded to 9.10.  But it has never worked well enough for me to depend on it.  Does anyone have any reliable experience with this software?  

After being patient for a very long time, I'm reluctantly throwing it out.  And this pains me very much, as I have to resort to accessing a Windows terminal server to run Outlook.  Of course my employer suffers the same short sightedness as most by insisting on standardizing on Outlook and Exchange for our corporate email.  

Of all the promise and wonderful tools on Linux, you'd think someone could write an outlook clone that works.  I don't need all the fancy features, just the basics, in a reliable package.  I think it's one of the rare but great failings of Linux and open source  -- no reliable Outlook clone.  

-Steve

---

