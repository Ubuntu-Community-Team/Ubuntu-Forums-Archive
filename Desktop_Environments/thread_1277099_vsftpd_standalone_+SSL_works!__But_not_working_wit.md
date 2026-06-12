---
title: "vsftpd standalone +SSL works!  But not working with xinetd superserver. Please Help!"
date: 2009-09-27
forum: Desktop Environments
---

### Post by traylorre on 2009-09-27
[SIZE=2]Summary: When I insert **xinetd **as a superserver, I can connect to **xinetd **(I get the xinetd banner), but the connection to **vsftpd **fails.[/SIZE]

I have banged my head on this for two weeks now :confused: and am so excited to almost get my FTPS server up and running!  Here I am using FTPS which is FTP with SSL/TLS security.  

[I][B]Note that this is not SFTP (port 115), nor SSH or FTP via SSH (port 22)
[/B][/I]
Currently, I am able to connect to my linux box via vsftpd on standalone mode 
```
 **_vs__ftpd.conf_**
# do not bridge through superserver to connect with client
tcp_wrappers=NO
# standalone operation; listen for client on port 21
listen=YES
```I see in the connection log that encryption is enabled.
```
Command:    PROT P
Response:    200 PROT now Private.

```This tells me that vsftpd is a server and that my client connected directly to it.
[COLOR=DarkGreen]
[/COLOR] [COLOR=Red]**[COLOR=DarkGreen](client) -- FTP+SSL/TLS on port 21 ---> (vsftpd server)[/COLOR]**
[/COLOR] 
In this situation (standalone) I spawn the vsftpd server myself:
```
Network_Drive:/usr/sbin# vsftpd  /etc/vsftpd_scott.conf

```**Q1. **It seems that I am stuck with port 21/20 which is FTP/FTP_DATA.  **Is there a way to specify port 990 for SFTP when in standalone mode?**
[COLOR=DarkGreen]Answer : Embarassingly, it's right there in man vsftpg.conf:** listen_port**.  I don't know how I missed it.[/COLOR]

However, when I insert xinetd into this working picture as the super-server, then I cannot get the connection to bridge properly. 
**[COLOR=DarkGreen](client) -- FTP+SSL/TLS on port 990 --> (xinetd superserver)[COLOR=Red]--???-> [/COLOR](vsftpd server)[/COLOR]**

With **xinetd**, I understand that I should spawn **xinetd**, and that it will in turn spawn **vsftpd **as needed. So I kill ths **vsftpd **process, and spawn **xinetd**:
 ```
xinetd -d -f /etc/xinetd_scott.conf
```(-d is debug output to terminal; -f is to specify the xinetd configuration file)
 
Please assist as I am new to xinetd, or at least suggest the next step in debug I can try!  I have several ideas, please read on.

Here are my configuration files:
```
_**xinetd.conf**_
#defaults
#{
# commented defaults 
#}

 service ftps
{
#--------------------------------------------------------------------------------
    socket_type          = stream
    port                      = 990
    protocol                = tcp
# no=multithreaded; yes=singlethreaded
    wait            = no 

#--------------------------------------------------------------------------------
# determines the uid for the server process.  
# Ineffective if the effective user ID of xinetd is not super-user
    user            = root
# determines the gid for the server process.  
# If not specified, then group of user will be used (from /etc/passwd).  
# Ineffective if the effective user ID of xinetd is not super-user and if the groups attribute is not set to 'yes'
    group                   = root
# Yes=executed with access to the groups that the server's effective UID has access to.  
# No=server runs with no supplementaty groups.  Needed for many BSD systems.
    groups            = yes

#--------------------------------------------------------------------------------
    server            = /usr/local/sbin/vsftpd
    server_args        = /etc/vsftpd_scott.conf

#--------------------------------------------------------------------------------
    banner            = /etc/xinetd.banner  
# Displayed on successful connection
    banner_success          = /etc/xinetd_success.banner  
# Displayed on unsuccesful connection
    banner_fail             = /etc/xinetd_fail.banner 
    log_type                = file /var/log/xinetd_vsftpd.log 5K 20K
    log_on_success        += DURATION HOST USERID EXIT 
    log_on_failure         += HOST USERID ATTEMPT
# Limit to these times for access
#    access_times    = 2:00-8:59 12:00-23:59 

#--------------------------------------------------------------------------------
# Limits the total number of connections from ALL IP sources
    instances        = 10 
# Determines server priority.  check nice(3) for more info.  Can be negative
    nice            = 10  
# Limits the total number of connections from one IP source
    per_source        = 6   
# Linits the rate of incoming connections.  Connections per second; number of seconds to wait.
    cps            = 1 3 

#--------------------------------------------------------------------------------
}



``````
_**vsftpd.conf**_
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
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
xferlog_file=/var/log/xferlog

#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
idle_session_timeout=6000
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
ftpd_banner=Welcome to my ftpd_banner
banner_file=/etc/vsftpd.banner

# per user directory message
dirmessage_enable=YES
message_file=/etc/vsftpd.message

# uploaded files are ownership == 777 & ~unmask
anon_umask=077
local_umask=022

# YES = enable passive mode; NO = make server active
pasv_enable=YES

# specify the 
#pam_service_name=vsftpd

#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#d_email_file=/etc/vsftpd.banned_emails
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
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
# When "listen" directive is enabled, vsftpd runs in standalone mode and
# listens on IPv4 sockets. This directive cannot be used in conjunction
# with the listen_ipv6 directive.
listen=NO

# YES = use inted/xinetd; NO = do not use inetd/xinetd
tcp_wrappers=YES

#
# This directive enables listening on IPv6 sockets. To listen on IPv4 and IPv6
# sockets, you must run two copies of vsftpd whith two configuration files.
# Make sure, that one of the listen options is commented !!
#listen_ipv6=YES

#rsa_cert_file=/usr/share/ssl/certs/vsftpd_cert.pem
#rsa_private_key_file=/usr/share/ssl/certs/vsftpd_private_key.pem
#rsa_cert_file=/usr/share/ssl/certs/vsftpd_both.pem

rsa_cert_file=/usr/share/ssl/certs/server.crt
rsa_private_key_file=/usr/share/ssl/certs/server.key

log_ftp_protocol=YES

ssl_enable=YES
implicit_ssl=NO

force_local_data_ssl=YES
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=YES

use_localtime=YES


```These are the logs that I got when connecting with xinetd:
```

Network_Drive:/usr/sbin# xinetd -d -f /etc/xinetd_scott.conf
Service defaults
        Bind = All addresses.
        Only from: All sites
        No access: No blocked sites
        No logging

Service configuration: ftps
        id = ftps
        flags = IPv4
        socket_type = stream
        Protocol (name,number) = (tcp,6)
        port = 990
        Instances = 10
        wait = no
        user = 0
        group = 0
        Groups = yes
        Nice = 10
        CPS = max conn:1 wait:3
        PER_SOURCE = 6
        Bind = All addresses.
        Server = /usr/local/sbin/vsftpd
        Server argv = vsftpd /etc/vsftpd_scott.conf
        Only from: All sites
        No access: No blocked sites
        Logging to file: /var/log/xinetd_vsftpd.log (soft=5120 hard=20480)
        Log_on_success flags = HOST DURATION EXIT USERID
        Log_on_failure flags = HOST ATTEMPT USERID

09/9/27@19:14:24: DEBUG: 9501 {cnf_start_services} Started service: ftps
09/9/27@19:14:24: DEBUG: 9501 {cnf_start_services} mask_max = 6, services_started = 1
09/9/27@19:14:24: NOTICE: 9501 {main} xinetd Version 2.3.14 started with libwrap loadavg                                                                      options compiled in.
09/9/27@19:14:24: NOTICE: 9501 {main} Started working: 1 available service
09/9/27@19:14:24: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:16:54: DEBUG: 9501 {main_loop} select returned 1
09/9/27@19:16:54: ERROR: 9501 {banner_always} service = ftps, open of banner yes failed
09/9/27@19:16:54: DEBUG: 9501 {server_start} Starting service ftps
09/9/27@19:16:54: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:17:00: DEBUG: 9501 {main_loop} select returned 1
09/9/27@19:17:00: ERROR: 9501 {banner_always} service = ftps, open of banner yes failed
09/9/27@19:17:00: DEBUG: 9501 {server_start} Starting service ftps
09/9/27@19:17:00: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:17:24: DEBUG: 9571 {exec_server} duping 8
09/9/27@19:17:25: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:17:25: DEBUG: 9501 {main_loop} select returned 1
09/9/27@19:17:25: DEBUG: 9501 {check_pipe} Got signal 17 (Child exited)
09/9/27@19:17:25: DEBUG: 9501 {child_exit} waitpid returned = 9571
09/9/27@19:17:25: DEBUG: 9501 {server_end} ftps server 9571 died
09/9/27@19:17:25: DEBUG: 9501 {svc_postmortem} Checking log size of ftps service
09/9/27@19:17:25: INFO: 9501 {conn_free} freeing connection
09/9/27@19:17:25: DEBUG: 9501 {child_exit} waitpid returned = 0
09/9/27@19:17:25: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:17:30: DEBUG: 9576 {exec_server} duping 8
09/9/27@19:17:30: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:17:30: DEBUG: 9501 {main_loop} select returned 1
09/9/27@19:17:30: DEBUG: 9501 {check_pipe} Got signal 17 (Child exited)
09/9/27@19:17:30: DEBUG: 9501 {child_exit} waitpid returned = 9576
09/9/27@19:17:30: DEBUG: 9501 {server_end} ftps server 9576 died
09/9/27@19:17:30: DEBUG: 9501 {svc_postmortem} Checking log size of ftps service
09/9/27@19:17:30: INFO: 9501 {conn_free} freeing connection
09/9/27@19:17:30: DEBUG: 9501 {child_exit} waitpid returned = -1
09/9/27@19:17:30: DEBUG: 9501 {main_loop} active_services = 1
09/9/27@19:20:41: NOTICE: 9501 {general_handler} Unexpected signal 2 (Interrupt)

``````

[B]_FileZilla, connecting via SSL explicit on port 990_
[/B]Status:    Selected port usually in use by a different protocol.
Status:    Connecting to 192.168.0.150:990...
Status:    Connection established, waiting for welcome message...
[COLOR=DarkGreen]Response:    Welcome to xinetd_success.banner[/COLOR]
[COLOR=Red]Error:    Could not connect to server[/COLOR]
Status:    Waiting to retry...
Status:    Connecting to 192.168.0.150:990...
Status:    Connection established, waiting for welcome message...
[COLOR=DarkGreen]Response:    Welcome to xinetd_success.banner[/COLOR]
[COLOR=Red]Error:    Could not connect to server[/COLOR]

``````

_**xinetd log of ftps service:**_
09/9/27@19:16:54: START: ftps from=192.168.0.195
09/9/27@19:17:00: START: ftps from=192.168.0.195
09/9/27@19:17:25: EXIT: ftps signal=13 duration=31(sec)
09/9/27@19:17:30: EXIT: ftps signal=13 duration=30(sec)

``````

[U][B]vsftpd log:
[/B][/U]
*... *chirp chirp* ... nothing in here ...*


```What I can gather is:
-- The ftps service of xinetd successfully passed the banner contents to FileZilla (because I see it in FileZilla output).  So client -> xientd worked.

-- There is no log in vsftpd log, so this suggests that vsftpd did not get spawned.

Some notes:
--When in standalone mode (no **xinetd**) connecting via SSL/implicit (implicit_ssl=YES) as well as SSL/explicit (implicit_ssl=NO) both work.
However, when I use **xinetd**, both fail, but I note that with SSL/explicit I at least get the banner and then fail to connect.  With SSL/implicit, I do not get the banner at all.

My questions, please help :popcorn::
**Q1. **It seems that I am stuck with port 21/20 which is FTP/FTP_DATA. **Is there a way to specify port 990 for SFTP when in standalone mode?**
[COLOR=DarkGreen]Answer : Embarassingly, it's right there in man vsftpg.conf: **listen_port**.  I don't know how I missed it.[/COLOR]

**Q2.** I verified that xinetd is pointing to vsftpd correctly in xinetd_conf.  [B]Why is xinetd not spawning vsftpd like it should??
[/B][B]
Q3. [/B]I want to have some visibility or more logs so that I can debug this.  [B]In what ways can I debug the interaction between xinetd and vsftpd?  
[/B]
I tried
```
strace xinetd -d -f /etc/xinetd_scott.conf
``` but I got a vomit of logs with repeating errors  (Yes, I have no idea how to use strace so please advise :)).

I should mention that I am running **Debian Lenny** on a **Dlink DNS-323** Network Area Storage unit running on an ARM processor. I then used apt-get to get Lenny, then the latest version of all softwares mentioned above and compiled locally (to get SSL support in vsftpd and xinetd).

Thank you in advance.
Scott

---

### Post by traylorre on 2009-09-28
Summary:
[COLOR=Red]**[COLOR=DarkGreen]WORKS : (client) --> FTP+SSL/TLS  ---> (vsftpd server)  [/COLOR]**[/COLOR]
**[COLOR=Red]FAILS [/COLOR]: [COLOR=DarkGreen](client) --> FTP+SSL/TLS [COLOR=Red]--> (xinetd superserver)[/COLOR][/COLOR][COLOR=Red]--???->[/COLOR]****[COLOR=DarkGreen](vsftpd server)[/COLOR]**

In [COLOR=DarkGreen]**PASS **[/COLOR]case, **vsftpd **connects with FTP + explicit SSL and works.  Also works with FTP + implicit SSL.  Great!

It [COLOR=Red]**FAIL **[/COLOR]case, **vsftpd **does not log anything, and looks like it was never triggered.  
In **client (FileZilla, CuteFTP)** log, I see my **xinetd **message banner get returned.  There is absolutely nothing in **vsftpd **log (look like it didn't get spawned).

---

### Post by traylorre on 2009-09-28
Do I need a wrapper that I may be missing?

In particular, do I need to install PAM ([*[I]Pluggable Authentication Modules*[/I]]("http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules"))?

Thanks.

---

### Post by traylorre on 2009-09-28
I have been hammering xinetd with CuteFTP and I finally got the following log.

First it asked me to accept the certificate from vsftpd (yay!) then it had this error.  

[COLOR=DarkGreen]STATUS:>      [9/27/2009 9:51:36 PM] Connecting to FTP server... 192.168.0.150:21 (ip = 192.168.0.150)...
STATUS:>      [9/27/2009 9:51:36 PM] Socket connected. Waiting for welcome message...
        [9/27/2009 9:52:06 PM] Welcome to the xinetd banner
        Welcome to xinetd_success.banner[/COLOR]
        **[COLOR=Red]500 OOPS: tcp_wrappers is set to YES but no tcp wrapper support compiled in[/COLOR]**
[COLOR=Red]ERROR:>       [9/27/2009 9:52:06 PM] WARNING! Invalid FTP reply received: 3 digit number expected at the beginning of the server reply.
ERROR:>       [9/27/2009 9:52:06 PM] Syntax error: command unrecognized.[/COLOR]

```

_**vsftpd.log**_
Sun Sep 27 21:56:20 2009 [pid 13588] CONNECT: Client "192.168.0.195"
Sun Sep 27 21:56:20 2009 [pid 13588] FTP response: Client "192.168.0.195", "220-Welcome to
my vsftpd banner file"
Sun Sep 27 21:56:20 2009 [pid 13588] FTP response: Client "192.168.0.195", "220 "
Sun Sep 27 21:56:20 2009 [pid 13588] FTP command: Client "192.168.0.195", "AUTH SSL"
Sun Sep 27 21:56:20 2009 [pid 13588] FTP response: Client "192.168.0.195", "234 Proceed wit
h negotiation."
[COLOR=Red]Sun Sep 27 21:56:23 2009 [pid 13588] DEBUG: Client "192.168.0.195", "SSL_accept failed: err
or:00000000:lib(0):func(0):reason(0)"[/COLOR]

```This is suspicious...  I suspect a bug with FileZilla, because it works in CuteFTP (below)

```

listen=NO
tcp_wrappers=NO
rsa_cert_file=/usr/share/ssl/certs/server.crt
rsa_private_key_file=/usr/share/ssl/certs/server.key
log_ftp_protocol=YES

ssl_enable=YES
implicit_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=YES

```I connected in CuteFTP with 
I tried CuteFTP, and the connection works.  Settings: "FTP with SSL Auth SSL Explicit 21"  Port 21

The problem is that I need to use this on a commercial system and would like it to be free (CuteFTP is 30 shareware)

I tried CoreFTP, FireFTP, and they all do not work.

---

### Post by traylorre on 2009-09-29
Well I apologize for posting in an Ubuntu forum with my Debian question... I thought they were synonyms sort of like Red Hat and CentOS.

Anyways, I finally resolved the issue.  In a nutshell, any of the banner directives in vsftpd.conf work when it is just vsftpd, but who knew that if you add xinetd to the system then any of the banner directives will break it.

Full post here: [http://www.linuxquestions.org/questions/linux-networking-3/xinetd-2.3.14-could-not-bind-listening-ipv4-socket-to-vsftpd-2.2.0-on-deb5.0.3-758298/#post3700275]("http://www.linuxquestions.org/questions/linux-networking-3/xinetd-2.3.14-could-not-bind-listening-ipv4-socket-to-vsftpd-2.2.0-on-deb5.0.3-758298/#post3699754")

You can find there verbatim my .conf files, my explicit setup, as well as personal experience on which of the 4 FTP clients worked and which didn't.  If you are troubleshooting xinetd <-> vsftpd issues, then this could very likely help you.

Thanks for those who viewed ;)

---

