---
title: "Changing AnonDirName for CUPS-PDF"
date: 2008-05-08
forum: Desktop Environments
---

### Post by iimess on 2008-05-08
I followed _[this post](http://ubuntuforums.org/showpost.php?p=1941142&postcount=84)_ to change the PDF output directory for remote users. After the change the printing appears to work still, but I can't get any output files. The pdf seems to be created but then immediately deleted:

/var/log/cups/cups-pdf_log:
```
Thu May  8 11:35:39 2008  [DEBUG] switching to new gid (lpadmin)
Thu May  8 11:35:39 2008  [DEBUG] initialization finished (v2.4.6)
Thu May  8 11:35:39 2008  [DEBUG] unknown user (remoteuser)
Thu May  8 11:35:39 2008  [DEBUG] trying lower case user name (remoteuser)
Thu May  8 11:35:39 2008  [DEBUG] unknown user (remoteuser)
Thu May  8 11:35:39 2008  [DEBUG] output directory name generated (/home/public/PDF)
Thu May  8 11:35:39 2008  [DEBUG] spoolfile name created (/var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] source stream ready
Thu May  8 11:35:39 2008  [DEBUG] destination stream ready (/var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] owner set for spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] found beginning of postscript code (%!PS-Adobe-3.0)
Thu May  8 11:35:39 2008  [DEBUG] now extracting postscript code
Thu May  8 11:35:39 2008  [DEBUG] found title in ps code (Microsoft Office Outlook - Memo Style)
Thu May  8 11:35:39 2008  [DEBUG] found end of postscript code (%%EOF)
Thu May  8 11:35:39 2008  [DEBUG] all data written to spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] trying to use PS title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:35:39 2008  [DEBUG] removing trailing newlines from title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:35:39 2008  [DEBUG] removing special characters from title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:35:39 2008  [DEBUG] title successfully retrieved (Microsoft_Office_Outlook_-_Memo_Style)
Thu May  8 11:35:39 2008  [DEBUG] input data read from stdin
Thu May  8 11:35:39 2008  [DEBUG] output filename created (/home/public/PDF/Microsoft_Office_Outlook_-_Memo_Style.pdf)
Thu May  8 11:35:39 2008  [DEBUG] ghostscript commandline built (/usr/bin/gs -q -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="/home/public/PDF/Microsoft_Office_Outlook_-_Memo_Style.pdf" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f /var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] output file unlinked (/home/public/PDF/Microsoft_Office_Outlook_-_Memo_Style.pdf)
Thu May  8 11:35:39 2008  [DEBUG] TMPDIR set for GhostScript (/var/tmp)
Thu May  8 11:35:39 2008  [DEBUG] entering child process
Thu May  8 11:35:39 2008  [DEBUG] GID set for current user
Thu May  8 11:35:39 2008  [DEBUG] UID set for current user (nobody)
Thu May  8 11:35:39 2008  [DEBUG] user information prepared
Thu May  8 11:35:39 2008  [DEBUG] ghostscript has finished (256)
Thu May  8 11:35:39 2008  [DEBUG] waiting for child to exit
Thu May  8 11:35:39 2008  [DEBUG] spoolfile unlinked (/var/spool/cups-pdf/SPOOL/cups2pdf-19688)
Thu May  8 11:35:39 2008  [DEBUG] all memory has been freed


```

/var/log/cups/error_log:
```
I [08/May/2008:11:35:00 -0700] Scheduler shutting down normally.
I [08/May/2008:11:35:00 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [08/May/2008:11:35:01 -0700] Listening to :::631 (IPv6)
I [08/May/2008:11:35:01 -0700] Listening to 0.0.0.0:631 (IPv4)
I [08/May/2008:11:35:01 -0700] Listening to /var/run/cups/cups.sock (Domain)
I [08/May/2008:11:35:01 -0700] Loaded configuration file "/etc/cups/cupsd.conf"
I [08/May/2008:11:35:01 -0700] Using default TempDir of /var/spool/cups/tmp...
I [08/May/2008:11:35:01 -0700] Configured for up to 100 clients.
I [08/May/2008:11:35:01 -0700] Allowing up to 100 client connections per host.
I [08/May/2008:11:35:01 -0700] Using policy "default" as the default!
I [08/May/2008:11:35:01 -0700] Full reload is required.
I [08/May/2008:11:35:01 -0700] Loaded MIME database from '/etc/cups': 36 types, 39 filters...
*** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
I [08/May/2008:11:35:01 -0700] Loading job cache file "/var/cache/cups/job.cache"...
I [08/May/2008:11:35:01 -0700] Full reload complete.
I [08/May/2008:11:35:01 -0700] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [08/May/2008:11:35:01 -0700] Listening to :::631 on fd 13...
I [08/May/2008:11:35:01 -0700] Listening to 0.0.0.0:631 on fd 14...
I [08/May/2008:11:35:01 -0700] Listening to /var/run/cups/cups.sock on fd 15...
I [08/May/2008:11:35:01 -0700] Resuming new connection processing...
I [08/May/2008:11:35:39 -0700] [Job 37] Adding start banner page "none".
I [08/May/2008:11:35:39 -0700] [Job 37] Adding job file of type application/postscript.
I [08/May/2008:11:35:39 -0700] [Job 37] Adding end banner page "none".
I [08/May/2008:11:35:39 -0700] [Job 37] Queued on "PDF" by "remoteuser".
I [08/May/2008:11:35:39 -0700] [Job 37] Started filter /usr/lib/cups/filter/pstops (PID 19686)
I [08/May/2008:11:35:39 -0700] [Job 37] Started backend /usr/lib/cups/backend/cups-pdf (PID 19688)
I [08/May/2008:11:35:39 -0700] [Job 37] Completed successfully.
I [08/May/2008:11:36:08 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19770)
I [08/May/2008:11:36:10 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19773)

```

In /etc/cups/cups-pdf.conf:
```
AnonDirName /home/public/PDF
```
```
drwxrwxrwt 2 root root 4096 2008-05-07 19:06 /home/public/PDF
```

It worked before with the default directory /var/spool/cups-pdf/ANONYMOUS

Successful /var/log/cups/cups-pdf_log:
```
Thu May  8 11:53:54 2008  [DEBUG] switching to new gid (lpadmin)
Thu May  8 11:53:54 2008  [DEBUG] initialization finished (v2.4.6)
Thu May  8 11:53:54 2008  [DEBUG] unknown user (remoteuser)
Thu May  8 11:53:54 2008  [DEBUG] trying lower case user name (remoteuser)
Thu May  8 11:53:54 2008  [DEBUG] unknown user (remoteuser)
Thu May  8 11:53:54 2008  [DEBUG] output directory name generated (/var/spool/cups-pdf/ANONYMOUS)
Thu May  8 11:53:54 2008  [DEBUG] spoolfile name created (/var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:54 2008  [DEBUG] source stream ready
Thu May  8 11:53:54 2008  [DEBUG] destination stream ready (/var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:54 2008  [DEBUG] owner set for spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:54 2008  [DEBUG] found beginning of postscript code (%!PS-Adobe-3.0)
Thu May  8 11:53:54 2008  [DEBUG] now extracting postscript code
Thu May  8 11:53:54 2008  [DEBUG] found title in ps code (Microsoft Office Outlook - Memo Style)
Thu May  8 11:53:54 2008  [DEBUG] found end of postscript code (%%EOF)
Thu May  8 11:53:54 2008  [DEBUG] all data written to spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:54 2008  [DEBUG] trying to use PS title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:53:54 2008  [DEBUG] removing trailing newlines from title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:53:54 2008  [DEBUG] removing special characters from title (Microsoft Office Outlook - Memo Style)
Thu May  8 11:53:54 2008  [DEBUG] title successfully retrieved (Microsoft_Office_Outlook_-_Memo_Style)
Thu May  8 11:53:54 2008  [DEBUG] input data read from stdin
Thu May  8 11:53:54 2008  [DEBUG] output filename created (/var/spool/cups-pdf/ANONYMOUS/Microsoft_Office_Outlook_-_Memo_Style.pdf)
Thu May  8 11:53:54 2008  [DEBUG] ghostscript commandline built (/usr/bin/gs -q -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="/var/spool/cups-pdf/ANONYMOUS/Microsoft_Office_Outlook_-_Memo_Style.pdf" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f /var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:54 2008  [DEBUG] output file unlinked (/var/spool/cups-pdf/ANONYMOUS/Microsoft_Office_Outlook_-_Memo_Style.pdf)
Thu May  8 11:53:54 2008  [DEBUG] TMPDIR set for GhostScript (/var/tmp)
Thu May  8 11:53:54 2008  [DEBUG] entering child process
Thu May  8 11:53:54 2008  [DEBUG] GID set for current user
Thu May  8 11:53:54 2008  [DEBUG] UID set for current user (nobody)
Thu May  8 11:53:54 2008  [DEBUG] user information prepared
Thu May  8 11:53:55 2008  [DEBUG] ghostscript has finished (0)
Thu May  8 11:53:55 2008  [DEBUG] file mode set for user output (/var/spool/cups-pdf/ANONYMOUS/Microsoft_Office_Outlook_-_Memo_Style.pdf)
Thu May  8 11:53:55 2008  [DEBUG] no postprocessing
Thu May  8 11:53:54 2008  [DEBUG] waiting for child to exit
Thu May  8 11:53:55 2008  [DEBUG] spoolfile unlinked (/var/spool/cups-pdf/SPOOL/cups2pdf-20192)
Thu May  8 11:53:55 2008  [DEBUG] all memory has been freed

```


I see that when it fails, the log has "ghostscript has finished (256)". Where can I find the return values of gs? It's not in the man page.

---

### Post by iimess on 2008-05-12
Anyone?

---

### Post by mannheim on 2008-05-13
Perhaps it has to do with apparmor. You could look at  /etc/apparmor.d/usr.sbin.cupsd. It has a line:
```
 /var/spool/cups-pdf/** rw,

```
Try adding another line
```
/home/public/** rw,
```
or some such.

EDIT: This file location is for Ubuntu 8.04. I think that the layout has changed since Ubuntu 7.10; and earlier than that there was no apparmor by default.

---

