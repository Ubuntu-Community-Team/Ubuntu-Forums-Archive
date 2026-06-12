---
title: "Help with Proftpd - Fails at PASV"
date: 2006-01-09
forum: Desktop Environments
---

### Post by YaAqoB on 2006-01-09
Hi all.
I need some help.
I have setup Proftpd and when I log in across the network it works fine.
But when I log in via the internet it logs in, accepts my password and then fails at teh very end at the PASV command.
Inside my router I have port 21 forwarded to my FTP server and also TCP Ports 60000-60015 forwarded to my FTP Server.
This is my FTP conf

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerIdent on "Welcome to James Haworth's Ubuntu Web Server. Please enter your username and password."
ServerName			"Ubuntu Web Server"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer 120
TimeoutStalled 120
TimeoutLogin 120
TimeoutIdle 1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

PassivePorts 60000 60014

MasqueradeAddress YourSiteName.com
MasqueradeAddress xx.xxx.xxx.xx

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Allow to restart a download
AllowStoreRestart		on

 MaxClients 10
 MaxClientsPerHost 1 "Sorry but you are already logged on."
 RequireValidShell off


# Port 21 is the standard FTP port.
  Port				1980


 ExtendedLog /var/log/ftp.log auth,all

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				ftp-user

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser ftpuser
DenyALL
</Limit>

<Directory> /var/www/ftpuser/>

 Umask 022 022
AllowOverwrite on
<Limit MKD XMKD RNRF RNTO DELE RMD XRMD STOR>
AllowAll
</Limit>

</Directory>


Anyone have any ideas here?

Cheers

---

### Post by xyvian on 2008-02-08
I am having the same issues. anyone have a solution to this?

---

