---
title: "cups ignoring system v interfaces"
date: 2009-01-12
forum: General Help
---

### Post by jezndi on 2009-01-12
Just installed 8.04 server - tried to set up a printer to use a system v interface script (had to create /etc/cups/interfaces), but cups just seems to ignore the script.

same script is handled just dandy on 6.04 and earlier versions, and on other
older linuxes I've uesd.

Cups web interface shows the printer as "raw", not "local system v" printer 
which is what I've seen on other sytems. cupsd has been restarted several times.

Tried putting debug in cupsd, but it doesn't say much:

D [12/Jan/2009:19:55:49 +0000] Print-Job ipp://localhost/printers/test
D [12/Jan/2009:19:55:49 +0000] print_job: auto-typing file...
D [12/Jan/2009:19:55:49 +0000] add_job: requesting-user-name="root"
I [12/Jan/2009:19:55:49 +0000] [Job 2] Adding start banner page "none".
D [12/Jan/2009:19:55:49 +0000] Discarding unused job-created event...
I [12/Jan/2009:19:55:49 +0000] [Job 2] Adding job file of type text/plain.
I [12/Jan/2009:19:55:49 +0000] [Job 2] Adding end banner page "none".
I [12/Jan/2009:19:55:49 +0000] [Job 2] Queued on "test" by "root".
D [12/Jan/2009:19:55:49 +0000] [Job 2] hold_until = 0
D [12/Jan/2009:19:55:49 +0000] [Job 2] Sending job to queue tagged as raw...
D [12/Jan/2009:19:55:49 +0000] Discarding unused printer-state-changed event...
D [12/Jan/2009:19:55:49 +0000] [Job 2] job-sheets=none,none
D [12/Jan/2009:19:55:49 +0000] [Job 2] banner_page = 0
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[0]="laser"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[1]="2"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[2]="root"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[3]="passwd"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[4]="1"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[5]="finishings=3 number-up=1 c job-uuid=urn:uuid:b0e0870f-8bed-3882-7a26-dbd315344816"
D [12/Jan/2009:19:55:49 +0000] [Job 2] argv[6]="/var/spool/cups/d00002-001"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[9]="SERVER_ADMIN=root@ns2"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.7"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[12]="TZ=Europe/London"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[13]="USER=root"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[16]="IPP_PORT=631"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[17]="CHARSET=utf-8"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[18]="LANG=en_GB.UTF8"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[19]="PPD=/etc/cups/ppd/laser.ppd"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[20]="RIP_MAX_CACHE=8m"
 [12/Jan/2009:19:55:49 +0000] [Job 2] envp[21]="CONTENT_TYPE=text/plain"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[22]="DEVICE_URI=file:/tmp/file"
D [12/Jan/2009:19:55:49 +0000] [Job 2] envp[23]="PRINTER=test"
I [12/Jan/2009:19:55:49 +0000] [Job 2] Started filter /usr/lib/cups/filter/gziptoany (PID 18848)
D [12/Jan/2009:19:55:49 +0000] Discarding unused job-state-changed event...
D [12/Jan/2009:19:55:49 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [12/Jan/2009:19:55:49 +0000] PID 18848 (/usr/lib/cups/filter/gziptoany) exited with no errors.
D [12/Jan/2009:19:55:49 +0000] Discarding unused job-progress event...
D [12/Jan/2009:19:55:49 +0000] [Job 2] File 0 is complete.
I [12/Jan/2009:19:55:49 +0000] [Job 2] Completed successfully.
D [12/Jan/2009:19:55:49 +0000] Discarding unused printer-state-changed event...
D [12/Jan/2009:19:55:49 +0000] Discarding unused job-completed event...
D [12/Jan/2009:19:55:49 +0000] cupsdCloseClient: 7

Anyone have any idea why cups ignores the script?

---

### Post by jezndi on 2009-01-14
One word: apparmor

Disabling apparmor (loaded by default it seems) resolves this issue 
and it's all tickety boo.

---

