---
title: "Ubuntu auditing"
date: 2006-09-29
forum: Desktop Environments
---

### Post by 00coday on 2006-09-29
I have been looking all over trying to find out how to turn on/configure auditing in Ubuntu.  I know that auditd is dead and has become part of the kernel, but I don't see it listed as one of the kernel modules.  There are no files on the machine that have the word audit in them.

Any help with getting this set up would be greatly appreciated](*,)

---

### Post by nthdegree on 2006-09-29
Audit AFAIK is directly compiled into the kernel, since AFAIK SELinux support is on in the kernel and that requires Audit.

---

### Post by 00coday on 2006-10-07
So where are the audit logs and how is the auditing configured?  Auditing on other systems (AIX/HP-UX) generally has to be set up by functions auditied and users to audit.  Not a file on the system that contains the string 'audit' (ie: auditd.conf)

---

