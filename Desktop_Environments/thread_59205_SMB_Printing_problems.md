---
title: "SMB Printing problems"
date: 2005-08-23
forum: Desktop Environments
---

### Post by stiivi on 2005-08-23
I am trying to print on a printer connected to a windows machine. I have configured the printer connections as: "Printer type: Network Printer - Windwos Printer (SMB)". When I try to print a test page or print from OO.org I get no output.

More information about the problem:

# cd /var/log/cups
# tail -f error_log
...
I [23/Aug/2005:10:36:14 +0200] Adding start banner page "none" to job 12.
I [23/Aug/2005:10:36:14 +0200] Adding end banner page "none" to job 12.
I [23/Aug/2005:10:36:14 +0200] Job 12 queued on 'Okipage-8w-Lite' by 'stevko'.
I [23/Aug/2005:10:36:14 +0200] Started filter /usr/lib/cups/filter/pstops (PID 17842) for job 12.
I [23/Aug/2005:10:36:14 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 17843) for job 12.
I [23/Aug/2005:10:36:14 +0200] Started backend /usr/lib/cups/backend/smb (PID 17844) for job 12.
E [23/Aug/2005:10:36:14 +0200] PID 17843 stopped with status 3!
I [23/Aug/2005:10:36:14 +0200] Hint: Try setting the LogLevel to "debug" to find out more.

In /usr/lib/cups/filter/foomatic-rip the exit code 3 is defined as:

my $EXIT_JOBERR = 3;          # job is defective

What does that mean? How should I make it work?

Thanks for any hints.

---

### Post by Franko30 on 2005-08-23
Maybe this thread helps:

[http://www.ubuntuforums.org/showthread.php?t=27736&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27736&page=1&pp=10)

It did for me - entering guest (German: gast) as username and no password in the configuration dialogue (System -> Administration -> Printing) helped.

---

### Post by stiivi on 2005-08-23
No luck for me, as it is no connection problem, but looks like foomatic-rip problem :-/

---

### Post by stiivi on 2005-08-23
More information ... I have enabled more debugging by LogLevel debug, as stated in the logs (well, after figuring out that it has to be set in cuspd.conf not in printers.conf). I am getting:

D [23/Aug/2005:23:22:14 +0200] [Job 21] Starting renderer
D [23/Aug/2005:23:22:14 +0200] [Job 21] JCL: <job data>
D [23/Aug/2005:23:22:14 +0200] [Job 21]
D [23/Aug/2005:23:22:14 +0200] [Job 21] renderer PID kid4=17793
D [23/Aug/2005:23:22:14 +0200] [Job 21] renderer command: (echo -n "AKEOKI PAPERSIZE=a4\nAKEOKI MANUALFEED=OFF\nAKEOKI PAPERWEIGHT=0\nAKEOKI GRAPHICS=OFF\nAKEOKI DARKNESS=0\n"; cat) 1>/dev/oki4drv 2>/dev/null
D [23/Aug/2005:23:22:14 +0200] [Job 21] sh: /dev/oki4drv: Permission denied
D [23/Aug/2005:23:22:14 +0200] [Job 21] renderer return value: 1
D [23/Aug/2005:23:22:14 +0200] [Job 21] renderer received signal: 1
D [23/Aug/2005:23:22:14 +0200] [Job 21] Process dying with "Possible error on renderer command line or PostScript error. Check options.", exit stat: 3
D [23/Aug/2005:23:22:14 +0200] [Job 21] Possible error on renderer command line or PostScript error. Check options.

but I have no /dev/oki4drv. why should I? it is SAMBA. Or is there something like symling to a file expected or what?

---

