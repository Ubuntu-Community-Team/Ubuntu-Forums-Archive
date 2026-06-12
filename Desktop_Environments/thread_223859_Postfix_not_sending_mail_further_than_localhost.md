---
title: "Postfix not sending mail further than localhost"
date: 2006-07-27
forum: Desktop Environments
---

### Post by TheCross on 2006-07-27
Hello,

I am having some problems with postfix.  I am able to send mail locally, but never externally.  I am using opera as my mail client. SMTP is set to localhost port 25. It was working perfectly fine before I upgraded to 6.06.

Here is a chunk from mail.log:

> Jul 26 19:45:29 localhost postfix/smtpd[6935]: connect from localhost.localdomain[127.0.0.1]
Jul 26 19:45:29 localhost postfix/smtpd[6935]: DFCE5833E2: client=localhost.localdomain[127.0.0.1]
Jul 26 19:45:29 localhost postfix/cleanup[6938]: DFCE5833E2: message-id=<op.tda7p3q03kzz4t@localhost.localdomain>
Jul 26 19:45:30 localhost postfix/smtpd[6935]: disconnect from localhost.localdomain[127.0.0.1]
Jul 26 19:45:50 localhost postfix/smtp[6939]: DFCE5833E2: to=<timtim_nz@hotmail.com>, relay=none, delay=21, status=deferred (Host or domain name not found. Name service error for name=hotmail.com type=MX: Host not found, try again)
Jul 26 20:07:49 localhost postfix/smtp[10086]: DFCE5833E2: to=<timtim_nz@hotmail.com>, relay=none, delay=1340, status=deferred (Host or domain name not found. Name service error for name=hotmail.com type=MX: Host not found, try again)
Jul 26 20:26:53 localhost authdaemond.mysql: restarting authdaemond children
Jul 26 20:26:53 localhost authdaemond.mysql: modules="authpam", daemons=5
Jul 26 20:26:58 localhost postfix/master[4952]: terminating on signal 15
Jul 26 20:31:04 localhost amavis[4273]: starting.  /usr/sbin/amavisd-new at localhost.localdomain amavisd-new-2.3.3 (20050822), Unicode aware
Jul 26 20:31:04 localhost amavis[4273]: Perl version               5.008007
Jul 26 20:31:04 localhost amavis[4287]: Module Amavis::Conf        2.043
Jul 26 20:31:04 localhost amavis[4287]: Module Archive::Tar        1.26
Jul 26 20:31:04 localhost amavis[4287]: Module Archive::Zip        1.16
Jul 26 20:31:04 localhost amavis[4287]: Module BerkeleyDB          0.27
Jul 26 20:31:04 localhost amavis[4287]: Module Compress::Zlib      1.41
Jul 26 20:31:04 localhost amavis[4287]: Module Convert::TNEF       0.17
Jul 26 20:31:04 localhost amavis[4287]: Module Convert::UUlib      1.051
Jul 26 20:31:04 localhost amavis[4287]: Module MIME::Entity        5.419
Jul 26 20:31:04 localhost amavis[4287]: Module MIME::Parser        5.419
Jul 26 20:31:04 localhost amavis[4287]: Module MIME::Tools         5.419
Jul 26 20:31:04 localhost amavis[4287]: Module Mail::Header        1.62
Jul 26 20:31:04 localhost amavis[4287]: Module Mail::Internet      1.62
Jul 26 20:31:04 localhost amavis[4287]: Module Net::Cmd            2.26
Jul 26 20:31:04 localhost amavis[4287]: Module Net::SMTP           2.29
Jul 26 20:31:04 localhost amavis[4287]: Module Net::Server         0.90
Jul 26 20:31:04 localhost amavis[4287]: Module Time::HiRes         1.66
Jul 26 20:31:04 localhost amavis[4287]: Module Unix::Syslog        0.100
Jul 26 20:31:04 localhost amavis[4287]: Amavis::DB code    loaded
Jul 26 20:31:04 localhost amavis[4287]: Amavis::Cache code loaded
Jul 26 20:31:04 localhost amavis[4287]: SQL base code      NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: SQL::Log code      NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: SQL::Quarantine    NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: Lookup::SQL  code  NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: Lookup::LDAP code  NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: AM.PDP prot  code  NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: SMTP-in prot code  loaded
Jul 26 20:31:04 localhost amavis[4287]: ANTI-VIRUS code    NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: ANTI-SPAM  code    NOT loaded
Jul 26 20:31:04 localhost amavis[4287]: Unpackers  code    loaded
Jul 26 20:31:04 localhost amavis[4287]: Found $file            at /usr/bin/file
Jul 26 20:31:04 localhost amavis[4287]: No $dspam,             not using it
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .mail
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .asc 
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .uue 
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .hqx 
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .ync 
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .F    tried: unfreeze, freeze -d, melt, fcat
Jul 26 20:31:04 localhost amavis[4287]: Found decoder for    .Z    at /bin/uncompress
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .gz  
Jul 26 20:31:04 localhost amavis[4287]: Found decoder for    .bz2  at /usr/bin/bzip2 -d
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .lzo  tried: lzop -d
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .rpm  tried: rpm2cpio.pl, rpm2cpio
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .cpio tried: pax
Jul 26 20:31:04 localhost amavis[4287]: Found decoder for    .cpio at /bin/cpio
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .tar  tried: pax
Jul 26 20:31:04 localhost amavis[4287]: Found decoder for    .tar  at /bin/cpio
Jul 26 20:31:04 localhost amavis[4287]: Found decoder for    .deb  at /usr/bin/ar
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .zip 
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .rar  tried: rar, unrar
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .arj  tried: arj, unarj
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .arc  tried: nomarch, arc
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .zoo  tried: zoo
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .lha  tried: lha
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .doc  tried: ripole
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .cab  tried: cabextract
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .tnef
Jul 26 20:31:04 localhost amavis[4287]: Internal decoder for .tnef
Jul 26 20:31:04 localhost amavis[4287]: No decoder for       .exe  tried: rar, unrar; lha; arj, unarj
Jul 26 20:31:05 localhost amavis[4287]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.27, libdb 4.3
Jul 26 20:31:07 localhost postgrey[4363]: Process Backgrounded 

If anybody could shed some light on this it would be greatly appreciated.

Thanks.
tc

---

### Post by TheCross on 2006-07-27
Anybody???

---

