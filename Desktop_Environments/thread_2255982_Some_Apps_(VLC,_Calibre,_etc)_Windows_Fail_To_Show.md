---
title: "Some Apps (VLC, Calibre, etc) Windows Fail To Show in 14.04, After Update"
date: 2014-12-09
forum: Desktop Environments
---

### Post by easygoing on 2014-12-09
Hi,
I have been using Ubuntu 14.04 quite happily for some time.
Two weeks ago, all of a sudden, the system took several minutes to boot up, and it took longer for mouse cursor to show up.
This is the time that I found that many applications cannot have their windows displayed. For example, I started VLC. I can see a carat in the VLC icon in the task bar, indicating that an instance of VLC is started. But I cannot see the VLC window on my desktop.
I updated my system, un-install and re-install VLC, without any improvement.
I found the same thing with Calibre.
However, terminal, Firefox, and other application works normally.
Is it possible that some system update break VLC, Calibre, and other applications?

---

### Post by ajgreeny on 2014-12-09
Try starting the errant applications in terminal.  You will probably get some error messages which you can then ask us about again.

---

### Post by easygoing on 2014-12-10
When I run VLC from command line, I got this:

$ vlc
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xd34118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

It seems normal. Just no application window showing up. The task bar and notification bar looks OK. I can even access the pop-up menu from the top right notification area.

---

### Post by mc4man on 2014-12-10
both vlc & calibre use qt4 in some manner. Is the same true for any other affected app?

---

