---
title: "KDE beta and Firefox crash"
date: 2008-06-05
forum: Desktop Environments
---

### Post by TheUnabeefer on 2008-06-05
I hope I posted this under the right section.  First of all, I have used Gentoo for YEARS and Slack before that, so I am relatively new to Ubuntu (and loving it intently, for the record)...

I am on the KDE4 hack of Kubuntu 8.04, and I upgraded to KDE 4.1beta1 using one of the repositories suggested in another thread.  It all seemed to go quite smooth and run really well, and there were no problems until this started happening:

When in Firefox, I open the "Save As" dialog for a file, Firefox crashes.  The same happens when attempting to attach a file in Thunderbird, as soon as it tries to open the file browser dialog.  I have just now (as in before I started this sentence) tried running Gimp, and that doesn't even want to start...

Those are the only real GTK based applications I use (oh, and Audacity), so i don't have all of Gnome installed, just KDE4... but this is only a problem in GTK apps running in the new beta.

Anyone else have this problem or know what I could try to fix it??  I have run them all in a terminal to see if it gave me any error, but all I got form them all was "Segmentation Fault"

Any help would be appareciated.  I may just downgrade until it's in the official repositories, but the beta 4.1 fixed a LOT of the annoyances I had with 4.0.4.  :(

---

### Post by TheUnabeefer on 2008-06-05
Someone helped me through another medium...  apparently it's an issue with gtkqt.  Hopefully it will be fixed eventually, because gtk apps now look ugly without it.  :KS

---

### Post by Dread Knight on 2008-11-28
> **TheUnabeefer said:**
> I hope I posted this under the right section.  First of all, I have used Gentoo for YEARS and Slack before that, so I am relatively new to Ubuntu (and loving it intently, for the record)...

I am on the KDE4 hack of Kubuntu 8.04, and I upgraded to KDE 4.1beta1 using one of the repositories suggested in another thread.  It all seemed to go quite smooth and run really well, and there were no problems until this started happening:

When in Firefox, I open the "Save As" dialog for a file, Firefox crashes.  The same happens when attempting to attach a file in Thunderbird, as soon as it tries to open the file browser dialog.  I have just now (as in before I started this sentence) tried running Gimp, and that doesn't even want to start...

Those are the only real GTK based applications I use (oh, and Audacity), so i don't have all of Gnome installed, just KDE4... but this is only a problem in GTK apps running in the new beta.

Anyone else have this problem or know what I could try to fix it??  I have run them all in a terminal to see if it gave me any error, but all I got form them all was "Segmentation Fault"

Any help would be appareciated.  I may just downgrade until it's in the official repositories, but the beta 4.1 fixed a LOT of the annoyances I had with 4.0.4.  :(

I pretty much have the same problem, but i can start gimp. Launchpad, google etc etc are not very helpful on this one... and it's ******* annoying man... i'm a graphic artist... besides gimp, other apps are incompetent/full of bugs (krita for example).


Even tried removing gtk-qt engine and no luck so far... heh. Need help!

---

### Post by irish66 on 2008-11-30
Hi, my firefox keeps crashing too. That was one of the reasons I moved over from windows. I thought it would be better in Linux. But no, it crashes here too. I get segmentation fault too. But I found I don't have
gtk-qt installed. Is there any other reason I might get segmentation fault
M

---

### Post by ArcherNB on 2009-03-08
I am Having the Same Problem I guess ill have to use Konqeror for a while.

---

### Post by jasmines on 2009-08-07
Same issue, here, with firefox and thunderbird.
Gedit, another gtk application, won't even start, and crashes with segfault.
Googling I was convinced it's a gtk-qt related problem, but even removing the engine, the crashes continue.

---

### Post by jasmines on 2009-08-11
Bump!

---

### Post by jasmines on 2009-08-16
Maybe a un-completed upgrade of the gtk libraries... maybe two or more versions mixed... maybe due to a forced dist-upgrade...

Any ideas on how to go back?

---

### Post by jasmines on 2009-08-26
[http://bugzilla.gnome.org/show_bug.cgi?id=591606](http://bugzilla.gnome.org/show_bug.cgi?id=591606)

---

