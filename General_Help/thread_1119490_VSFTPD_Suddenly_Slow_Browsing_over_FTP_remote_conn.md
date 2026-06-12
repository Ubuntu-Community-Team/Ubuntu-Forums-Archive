---
title: "VSFTPD: Suddenly Slow Browsing over FTP remote connection"
date: 2009-04-08
forum: General Help
---

### Post by paulg1981 on 2009-04-08
Hello All,
I am experiencing painfully slow browsing over remote ftp connections using vsftpd. This issue seems to have come from nowhere as earlier today it was fast as lighting. 

FTPing to localhost from the box is very quick so it is a remote issue only.

The connection part of the ftp session is very fast but the client hangs (gftp and cuteftp pro) when retrieving a directory listing. Sometimes it takes over a minute to get a listing and sometimes it times out all together. 

There is nothing of interest in the /var/log/vsftpd.log just a bunch of successful connections and disconnections.

Here is my vsftpd.conf file:
> # Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
tcp_wrappers=YES
ssl_enable=YES
force_local_logins_ssl=NO
force_local_data_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=/root/vsftpd.pem
listen_port=49155
session_support=NO
pasv_min_port=61000
pasv_max_port=61500
pasv_promiscuous=YES
port_promiscuous=YES


The only entry in vsftpd.chroot_list is 'root' to allow root login (via ssl don't hate me :-8)


And here is a snippet of a cuteftp log:
> 		*** CuteFTP 8.3 - build Aug 25 2008 ***

STATUS:>  	[4/8/2009 12:53:51 AM] Getting listing ""...
STATUS:>  	[4/8/2009 12:53:51 AM] Connecting to FTP server... 67.222.136.172:49155 (ip = myipaddress)...
STATUS:>  	[4/8/2009 12:53:51 AM] Socket connected. Waiting for welcome message...
STATUS:>  	[4/8/2009 12:53:51 AM] Control socket info: (local)192.168.1.101:51372 - (peer)myipaddress:49155.
		[4/8/2009 12:53:51 AM] 220 (vsFTPd 2.0.6)
STATUS:>  	[4/8/2009 12:53:51 AM] Connected. Authenticating...
COMMAND:>	[4/8/2009 12:53:51 AM] USER transfertime
		[4/8/2009 12:53:51 AM] 331 Please specify the password.
COMMAND:>	[4/8/2009 12:53:51 AM] PASS *****
		[4/8/2009 12:53:51 AM] 230 Login successful.
STATUS:>  	[4/8/2009 12:53:51 AM] Login successful.
COMMAND:>	[4/8/2009 12:53:51 AM] PWD
		[4/8/2009 12:53:51 AM] 257 "/"
STATUS:>  	[4/8/2009 12:53:51 AM] Home directory: /
COMMAND:>	[4/8/2009 12:53:51 AM] FEAT
		[4/8/2009 12:53:51 AM] Informational Message Only:
		211-Features:
		 AUTH SSL
		 AUTH TLS
		 EPRT
		 EPSV
		 MDTM
		 PASV
		 PBSZ
		 PROT
		 REST STREAM
		 SIZE
		 TVFS
		 UTF8
		211 End
STATUS:>  	[4/8/2009 12:53:51 AM] This site supports features.
STATUS:>  	[4/8/2009 12:53:51 AM] This site supports SIZE.
STATUS:>  	[4/8/2009 12:53:51 AM] This site can resume broken downloads.
COMMAND:>	[4/8/2009 12:53:51 AM] REST 0
		[4/8/2009 12:53:51 AM] 350 Restart position accepted (0).
COMMAND:>	[4/8/2009 12:53:51 AM] PASV
		[4/8/2009 12:53:51 AM] 227 Entering Passive Mode (myipaddress,239,96)
COMMAND:>	[4/8/2009 12:53:51 AM] LIST -a
STATUS:>  	[4/8/2009 12:53:51 AM] Connecting FTP data socket... myipaddress:61280...
STATUS:>  	[4/8/2009 12:53:51 AM] Passive connection established.
STATUS:>  	[4/8/2009 12:53:51 AM] Data socket info: (local)192.168.1.101:51373 - (peer)myipaddress:61280.
		[4/8/2009 12:53:51 AM] 150 Here comes the directory listing.
		[4/8/2009 12:54:32 AM] 226 Directory send OK.
STATUS:>  	[4/8/2009 12:54:32 AM] Parsing FTP listing...
STATUS:>  	[4/8/2009 12:54:32 AM] -------------------------------------------
		drwxrwxrwx    2 1000     1000         4096 Apr 08 02:08 .
		drwxrwxrwx    2 1000     1000         4096 Apr 08 02:08 ..
		
STATUS:>  	[4/8/2009 12:54:32 AM] -------------------------------------------
STATUS:>  	[4/8/2009 12:54:32 AM] Parsing FTP listing finished.
STATUS:>  	[4/8/2009 12:54:32 AM] Directory listing completed.

I am 100% sure that I do NOT have a firewall/router issue on my end as I have another ubuntu box running vsftpd with the exact same configs that connects like lightening and gives no errors. And I have also tried connecting from another box with the same slow browsing symptoms :-(

Any advice or solutions that you could give would be most appreciated. Thanks for your help

---

### Post by pateta on 2009-05-19
I have the same problem, dir listing is very slow with ssl... i create a new certificate, firewall is okay... version vsftps 2.0.7...

---

### Post by ballal10 on 2011-02-10
hey guys,
 
has anyone found a solution to this issue?
 
I have the exact same problem.. ftp browsing between folders whilst connected to my ps3 is extremely slow, there's like a minutes delay everytime i browse through the different folders.
 
please help
 
cheers

---

