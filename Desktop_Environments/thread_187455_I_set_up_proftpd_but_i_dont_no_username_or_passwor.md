---
title: "I set up proftpd but i dont no username or password"
date: 2006-06-03
forum: Desktop Environments
---

### Post by CameronCalver on 2006-06-03
Hey i created a ftp server with proftpd following the instructions from  [http://www.ubuntuforums.org/showthread.php?t=79588]("http://www.ubuntuforums.org/showthread.php?t=79588")
and when i go into a browse and type 192.168.1.120 it says username and login but ii dont no my username or login becuse i dont remeber seting on this is my conf file

ServerType standalone
DefaultServer on
Umask 022
ServerName cameronsftp
ServerIdent on "My FTPD"
Bind "0.0.0.0"
ServerAdmin [email]suped_up_supra_01@hotmail.com[/email]
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
User cameron
Group cameron
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser cameroncalver
  AllowUser cameron
  DenyALL
</Limit>

<Anonymous /home/FTP-shared>
User cameroncalver
Group cameroncalver
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /home/FTP-shared/linux.png/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /home/FTP-sharedp>
User cameron
Group cameron
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /home/ftp/upload/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
 DenyAll
</Limit>
</Directory>
</Anonymous>

---

