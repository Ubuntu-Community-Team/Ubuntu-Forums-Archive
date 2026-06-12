---
title: "ClamTK - 3 viruses found, no way to deal with them"
date: 2009-06-18
forum: General Help
---

### Post by luiznetto on 2009-06-18
I'm running Hardy Heron. I just installed ClamTK, and I used it to scan my whole filesystem. After some 3 hours, that's what the program takes to run, I got the message:
Viruses found: 3
And that's it. No other information. Not the names of the viruses, or the infected files, or where to find them, nothing! I thought I made a mistake, perhaps I should have checked "Quarantine infected files" from the Options menu. So I did it again, and after three hours, I got the same message again:
Viruses found: 3
And again, no info at all about said viruses.
The program comes with no documentation, and on the Internet nothing can be found except some outdated README files that don't answer the question of where the found viruses are supposed to be saved after a scan, or where at least their names and locations are to be found.
Also, I have trouble understanding those options and what they mean. Like for example, View -> Manage histories, clean output, load scan preferences, save scan preferences; or Save to log, what does that mean?

I am using ClamTK 3.08. Thanks in advance for your help.
Luiz

---

### Post by Yellow Pasque on 2009-06-19
[http://www.clamav.net/doc/latest/html/node30.html](http://www.clamav.net/doc/latest/html/node30.html)
Also note that ClamAV is notorious for false positives.

---

### Post by luiznetto on 2009-06-19
Let me see if I understood: that means that, if I want to know more about the viruses that were found, I **have** to do in on the command line? I mean, I just redid the whole scan. It still says "Viruses found: 3", but I still see know way to access info about them. What can I do? This time I used the option "Save to log" in addition to "Scan hidden files", but still no indication of where the viruses are or what their names.

---

### Post by Chronon on 2009-06-19
I think only someone who uses that frontend can answer this question.  I use KlamAV and it always tries to quarantine files.  I always have to tell it not to because they end up being false positives (broken executable) from a build directory somewhere.

I don't have any experience with ClamTk, so I don't know what features it gives access to.

---

### Post by the_phenom on 2009-06-19
Go get the latest version of ClamTk - from [http://clamtk.sf.net]("http://clamtk.sf.net").

---

### Post by bootdoc on 2009-06-19
I doubt you have any viruses.  Clamtk comes with some sample files that may be the "problem".

---

### Post by bootdoc on 2009-06-19
try KlamAV.  Its a better front end.

---

### Post by cariboo on 2009-06-19
Clamav creates a log file in /var/log. To view the logs go to System-->Administration-->Log File Viewer. If you don't see the log in the left pane, go to File-->Open and select the log file you wan to view.

---

### Post by luiznetto on 2009-06-19
I finally found a hidden folder in my home directory, ~/.clamtk. This folder contains two files and two folders.
The first file is called first_run; it's a plain text document; it's empty.
The second file is called prefs; it's also a plain text document; its contents are:

DisplayAll=0
FollowLinks=0
Quarantine=0
SaveToLog=0
ScanHidden=0
SizeLimit=0

And the two folders are called history and viruses. The second one is empty. The first one contains two text files, jun-18-2009.log and jun-19-2009.log. The second one is because I just scanned my usb pen drive (/media/disk); no viruses were found. But the first one was for the scanning of my whole filesystem that I did yesterday. I show here only the beginning and the end of this file:

ClamTk, v3.08
Thu Jun 18 23:32:10 2009
ClamAV Signatures: 0
Directories Scanned:
/
/tmp
/sys
/lib
/etc
/bin
/dev
/proc
/sbin
/boot
/root
/media
...
Found 3 possible viruses (185180 files scanned).

/sys/slab/                              0000320/slab_size
/var/log/gdm/                           0.log.1
/var/lib/ucf/cache/                     etc

I just installed Klamav, but the problem with Klamav is, every time I try to scan my home directory with it, it enters an endless loop, gets stuck at "thumbnails" (maybe because it's following links?), and I don't know how to configure it to behave otherwise.

As for the_phenom's suggestion that I get the latest version of ClamTk, they have a .deb and a tarball version, but in that case I may have to upgrade my Clamav too. I don't know if there is a newer version of Clamav that can be installed in Hardy Heron.

---

