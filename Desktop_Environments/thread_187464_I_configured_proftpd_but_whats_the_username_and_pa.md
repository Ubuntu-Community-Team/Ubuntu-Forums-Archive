---
title: "I configured proftpd but whats the username and password"
date: 2006-06-03
forum: Desktop Environments
---

### Post by CameronCalver on 2006-06-03
Hey i configured proftpd but when i go [ftp://192.168.1.120](ftp://192.168.1.120) it says username and password but i dont no it this is my conf

ServerType standalone
DefaultServer on
UserAlias cameron userftp
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

### Post by BadDolphin on 2006-10-16
It seems like a great many of us have this problem, and no solution that I can find... my own config is below, and all authentication attempts fail.

My config file looks like this:

ServerName "Hoof of the Vengeful Cow"
ServerType standalone
DeferWelcome off
MultilineRFC2228 on
DefaultServer on
ShowSymlinks on
TimeoutNoTransfer 1200
TimeoutStalled 1200
TimeoutIdle 2400
DisplayLogin welcome.msg
DisplayFirstChdir .message
ListOptions "-l"
DenyFilter \*.*/
PersistentPasswd off
AuthPAMAuthoritative off
Port 2525
MaxInstances 12
User nobody
Group nogroup
Umask 022 022
AllowOverwrite on
Umask 022 022
MaxClients 4
MaxClientsPerHost 4
MaxClientsPerUser 4
MaxHostsPerUser 4
AuthAliasOnly off
UserAlias closet userftp
UseFtpUsers off
AllowStoreRestart on
DefaultRoot /home/FTP-shared
DefaultRoot ~

AccessGrantMsg "Welcome to the closet. Rock on."
ServerIdent on "I be serveridentin"

MaxLoginAttempts 5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>

RequireValidShell off

---

### Post by BadDolphin on 2006-10-16
I finally just rm'd the config file, installed gproftpd to help configure it, and added a few users.  Then I restarted proftpd, and tried again- now the connection fails altogether.  Before I could at least get the tcp socket but now even that fails (though so far I can't find a log entry giving any details).  So it seems that the gui isn't a solution either.

---

