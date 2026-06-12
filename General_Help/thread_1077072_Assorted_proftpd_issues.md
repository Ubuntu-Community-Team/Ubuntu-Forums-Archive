---
title: "Assorted proftpd issues"
date: 2009-02-22
forum: General Help
---

### Post by Dillius on 2009-02-22
I've been working on getting an FTP server together so I can dump a bunch of files I need backed up.

I've been working on configuring it to use TLS based on a guide ([http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)), but it doesn't seem to be working very well.

I can connect without TLS fine, which shouldn't occur as I have it set as required. Could I have another FTP program that may have been installed by default present? (Unlikely, as i have seen no port bind conflicts)

Trying to connect with TLS, from Filezilla on a windows machine or Cyberduck on an apple machine, gives me the following:

```
220 FTP Server ready.
AUTH TLS
500 AUTH not understood
220 FTP Server ready.
AUTH TLS
500 AUTH not understood
```

Connecting without TLS, or with SFTP works. I would prefer to not be able to connect without TLS (SFTP is fine), which I would expect to be happening with the required flag on.

My config file is as follows:

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
#ServerIdent on "VAULT FTP"
ServerAdmin ****
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40           
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
<IfModule mod_tls.c>
TLSEngine on
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
#TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem

TLSRSACertificateFile      /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile   /etc/proftpd/ssl/proftpd.key.pem

#TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
#TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem

#TLSRenegotiate required off
TLSVerifyClient off
TLSRequired on
</IfModule>

#<IfModule mod_ratio.c>
#Ratios off
#SaveRatios off
#RatioFile "/restricted/proftpd_ratios"
#RatioTempFile "/restricted/proftpd_ratios_temp"
#CwdRatioMsg "Please upload first!"
#FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
#ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
#LeechRatioMsg "Your ratio is unlimited."
#</IfModule>

#<Limit LOGIN>
#  DenyALL
#</Limit>

DefaultRoot ~
IdentLookups off
ServerIdent on "FTP Server ready."

#

# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf
```

A few bits commented out, and I was going to be using an independent tls.conf file but I saw no need.

Could anyone advise me on the problems I am having? I have searched around a bit but have had no luck, and would really appreciate it.

---

### Post by Dillius on 2009-02-22
I have tried tweaking my configuration files quite a bit, and haven't really had any change in message so far. I did notice that the message present by Filezilla trying to connect is slightly different than the Cyberduck connection message.

Cyberduck:

```
220 FTP Server ready.
AUTH TLS
500 AUTH not understood
220 FTP Server ready.
AUTH TLS
500 AUTH not understood
```

Filezilla:

```
Response:	220 FTP Server ready.
Command:	AUTH TLS
Response:	500 AUTH not understood
Command:	AUTH SSL
Response:	500 AUTH not understood
```

Really not all that different, but Filezilla shows TLS then SSL whereas Cyberduck seems to refer to TLS twice.

I'm still able to connect with basic FTP from both, which I'm trying not to allow.

---

