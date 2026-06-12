---
title: "Half Life 1 on CD issues"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by toasty_ghosty on 2007-08-04
Alright. I've been looking at as many howtos as I can and I am still running into issues. I recently reinstalled Wine to make sure that is ok, which I think it is, and now I am installing Half Life 1 from a cd. But the issue is I cannot seem to get SETUP.EXE to run. I disc is showing up on my desktop, which means its mounted, correct? Heres what I've done:

theking@theking-desktop:/media/cdrom0$ wine SETUP.EXE
wine: could not load L"c:\\windows\\system32\\SETUP.EXE": Module not found

theking@theking-desktop:~$ wine SETUP.EXEwine: could not load L"c:\\windows\\system32\\SETUP.EXE": Module not found

What am I supposed to be doing? BTW, I also have Winetools installed. If that helps.

---

### Post by DoktorSeven on 2007-08-04
$ cd 
$ wine /media/cdrom0/SETUP.EXE

That or grab Steam, validate your HL1 serial, and download it.

---

### Post by toasty_ghosty on 2007-08-04
THANK YOU! Wine is the only thing so far that has really hung me up after switching to Ubuntu. But one last question. As stupid as it is, after installation how do I run it? What all do I type in the terminal? Also, I don't think I have DirectX installed. Whenever I begin to play the game I hear things, but I cannot see anything? How would I come about doing that? Or is that not the problem?

---

### Post by hikaricore on 2007-08-04
> theking@theking-desktop:/media/cdrom0$ wine SETUP.EXE
wine: could not load L"c:\\windows\\system32\\SETUP.EXE": Module not found

^here you're trying to run an installer from /media/cdrom0.  If you open up Nautilus and browse to /media/cdrom0, is this the **actual location** of your _CD DRIVE_?

> theking@theking-desktop:~$ wine SETUP.EXE
wine: could not load L"c:\\windows\\system32\\SETUP.EXE": Module not found

^Here you're trying to run an installer from your home directory.  I doubt it lives there.

Winetools to the best of my knowledge is no longer useful in any way.

You need to be changing to the directory that actually contains the installer (aka your mounted CD location), otherwise it's not going to happen.

---

### Post by toasty_ghosty on 2007-08-04
This may sound extremely stupid, but if I right click on the cdrom drive itself it says this as its location:

computer:///

Now, I know that is not right. But how could I find that actual location? Sometimes this makes me feel so dumb.

---

### Post by hikaricore on 2007-08-04
If you open up the drive in Nautilus is should say it's location under the toolbar.

---

