---
title: "Clearing printer jobs..."
date: 2009-01-27
forum: General Help
---

### Post by Barriehie on 2009-01-27
I've just noticed that when printing I can click on the printer in the top panel and it can display all of the completed print jobs.  How can I clear this list???

TIA,
Barrie

---

### Post by icheyne on 2009-01-28
Use "Cancel All Jobs" in the CUPS web admin interface ([http://127.0.0.1:631](http://127.0.0.1:631)).

---

### Post by Barriehie on 2009-01-28
> **icheyne said:**
> Use "Cancel All Jobs" in the CUPS web admin interface ([http://127.0.0.1:631](http://127.0.0.1:631)).


Very cool!  I didn't know about that.

Thank You,
Barrie

Edit:  Hmm, can't find the thank you button or the 'solved' button...

---

### Post by kostkon on 2009-01-28
You can deselect the *View &#8594; Show Completed Jobs* option in the printer status window (I mean the window that appears when you click on the printer icon in the taskbar).

---

### Post by emarkay on 2009-03-30
I am asked for a password - and without one I get a blank screen when I try to "Cancel All"

Thus thius does not work for me:  See new post here with link to Launchapd bug report.

[http://ubuntuforums.org/showthread.php?p=6985264#post6985264](http://ubuntuforums.org/showthread.php?p=6985264#post6985264)

---

### Post by icheyne on 2009-03-31
Did you try your login password?

---

### Post by emarkay on 2009-04-03
OK that cleared thm in CUPS, but not  in "Document Status (My Print Jobs)"...

GRRRRRRR!

---

### Post by emarkay on 2009-04-05
Anyone?

---

### Post by Barriehie on 2009-11-01
Don't know how I found it but the list of jobs is in ***/var/log/cups/page_log*** I changed ***LogLevel none*** in the ***/etc/cups/cupsd.conf*** file but it's still logging everything...

Barrie

---

### Post by mdkersey on 2011-11-22
Open a terminal window and do the following:

cd  /var/log/cups
sudo rm *.gz

---

