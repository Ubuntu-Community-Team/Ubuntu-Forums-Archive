---
title: "Need help with Outlook contacts and CAD"
date: 2008-12-03
forum: General Help
---

### Post by StephenD on 2008-12-03
I just installed Ubuntu and have run into a few issues one is my contacts list.  Is there any program out there which will sync my Outlook contacts list with a similar program in Ubuntu by pulling the data from the Outlook file on my Windows partition?

And second can anyone suggest a good solid modeling application, something like SolidWorks.  I tried a few listed on another post without much luck and was hoping to get suggestions from people who have worked with those available.

---

### Post by MeURi on 2008-12-03
Outlook stores the contacts in a file with wab extension (could it be Windows Address Book?), so the simplest solution is to export your contacts under Windows, reboot, locate that file and import it under Thunderbird, Evolution, or the mail client of your choice. Maybe there already is a file storing your contacts, "hidden" somewhere under your Documents and Settings\<username>\ folder, but I don't remember properly.

This method, anyway, does not propagate the changes you make to your contact list (under Ubuntu) to Windows, since it could be seen as a simple file copy operation. And I don't know how to keep them in sync. Maybe you can do something of the sort using Thunderbird both in Windows and Ubuntu, and making Thunderbird under Ubuntu use the same profile folder used by Thunderbird under Windows. Anyway, I don't know how much is this advisable.

For the modelling application, I can't help you, I'm sorry.

---

### Post by linux_tech on 2008-12-03
[http://brlcad.org/](http://brlcad.org/)  - BRL-CAD/3DSolids/Linux/free
[http://www.varicad.com/](http://www.varicad.com/)  - 3DSolids/Linux/freetrial/ $640

---

### Post by StephenD on 2008-12-03
> Outlook stores the contacts in a file with wab extension (could it be Windows Address Book?), so the simplest solution is to export your contacts under Windows, reboot, locate that file and import it under Thunderbird, Evolution, or the mail client of your choice. Maybe there already is a file storing your contacts, "hidden" somewhere under your Documents and Settings\<username>\ folder, but I don't remember properly.

This method, anyway, does not propagate the changes you make to your contact list (under Ubuntu) to Windows, since it could be seen as a simple file copy operation. And I don't know how to keep them in sync. Maybe you can do something of the sort using Thunderbird both in Windows and Ubuntu, and making Thunderbird under Ubuntu use the same profile folder used by Thunderbird under Windows. Anyway, I don't know how much is this advisable.

For the modelling application, I can't help you, I'm sorry. 
Thanks for the reply, but not quite what I am looking for.  I was hoping for something that would propagate automatically, though I do believe that your method can go both ways, it is just annoying having to export and import everytime I make a change.
> **linux_tech said:**
> [http://brlcad.org/](http://brlcad.org/)  - BRL-CAD/3DSolids/Linux/free
[http://www.varicad.com/](http://www.varicad.com/)  - 3DSolids/Linux/freetrial/ $640
Thanks for the tip, Vericad looks a bit pricy, and BRL-CAD is not quite user friendly enough for me to learn easily.

---

### Post by MeURi on 2008-12-03
You're welcome.

And well, as I said before, you could try Thunderbird in Windows, and see if it can replace Outlook (I used Express, and Thunderbird is AGES ahead ;-)).

If you make the switch, you can use Thunderbird in Ubuntu as well, storing mails and everything in the Windows profile folder. So you will have a 'shared' address book, and also emails, calendars, extensions.

Before doing that, note that Thunderbird may behave differently under Win and Ubuntu, due to line endings and (maybe) different codepages. Investigate on this, and if Thunderbird behaves the same way regardless of what I said, you can proceed and try :-P

---

### Post by rated727 on 2009-01-12
A "thank you" goes out to MeURi

I wanted to move my email, contacts, calendar, etc. from my (in my opinion) 'lesser secure' Win XP installation on my wireless capable laptop.  Specifically, I wanted to move my email facility on my ethernet (wired connection) desktop box (running OpenSolaris).

I had no success with my attempts to export from MS Outlook (Thunderbird and Evolution seemed to only find message headers).  Whether the fault was with Outlook export, or Thunderbird / Evolution import is not important ... it didn't work.

'When in doubt' ... I check this forum.  It saves a lot of time that I could easily waste in useless experimentation or 'trial and (many) error'.

I hoped to confirm my suspicion that Thunderbird or Evolution (for Windows) would be capable. The reply from MeURi suggested (at least to me) that Thunderbird for XP would directly inherit Outlook data. I installed it.

Sure enough! I copied Thunderbird's 'Local Folders' from the laptop to a removable USB and transfered it to the OpenSolaris/Thunderbird installation. Total SUCCESS!

I have not configured Samba or any other file sharing between Win XP and the Solaris installation on this box.  As soon as I finish transferring all of the laptop's data (documents, spreadsheets, bookkeeping, wwweb-bookmarks, etc.) to programs that run under OpenSolaris or Ubuntu (on either of the desktop boxes), I'll be ready to to clear XP from the laptop to set it up for a dual-boot Solaris/Ubuntu. So why configure sharing when it's simple enough to use removable USB or rewritable CD? And regular data backup to rewrite CD is actually a good idea, even if I wasn't going to change OS.

A carpenter will tell you to "measure twice ... cut once."
With computers, you should "backup twice ... delete once (or never)."  There's nothing worse than finding out that your ONLY backup is corrupted beyond recovery (a.k.a. FUBAR).

---

### Post by MeURi on 2009-01-12
Glad you transferred your emails under Ubuntu without issues.

By the way, have you found any linux app for CAD?

---

