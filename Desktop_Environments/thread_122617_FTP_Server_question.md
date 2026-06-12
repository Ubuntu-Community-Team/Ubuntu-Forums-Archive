---
title: "FTP Server question"
date: 2006-01-28
forum: Desktop Environments
---

### Post by shawnzyoo on 2006-01-28
when i try to log on to my FTP server
(proftp)
and it appears my router is workign right
when i browse to 
[ftp://mysite.com:1980](ftp://mysite.com:1980)
i get the user and password prompt
and when i enter any user name and password that i thought was right
it tells me error 530 Login Incorrect
is there somethign that i am not setting up right?
i can post my proftpd.conf if it would be useful
thanks

---

### Post by ]Nbx*cmD[ on 2006-01-28
I have two pro-ftpd servers running, and another one at work, so i think i'll can help you (one or other config should work hehe), can you post your proftpd.conf please?

---

### Post by shawnzyoo on 2006-01-28
here is my proftpd.conf file
do you use any of your servers for web administration?
thanks for the help

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias friends userftp
UserAlias jesica userftp1
UserAlias shawn userftp2


ServerName			"foxhole"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

PassivePorts 62000 62100

MasqueradeAddress	foxhole.kicks-***.net

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		on

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp userftp1
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

---

### Post by ]Nbx*cmD[ on 2006-01-29
Hmm it seems correct, have you tried changing the port back to 21?
I'm using two of these for web :) You can visit my home server at [http://80.25.162.189](http://80.25.162.189)

---

### Post by shawnzyoo on 2006-01-29
i tried changing it back to port 21 and no luck
do i have to create certain user accounts for it?
or how should i create the user accounts?

---

### Post by ]Nbx*cmD[ on 2006-01-30
Well... user accounts should be the same, no need to change nothing :-k
Now i'm going to work, i'll take the proftpd.conf from there and i'll post it, maybe this way we can find a solution :)

---

### Post by frodon on 2006-01-30
shawnzyoo, read that : [http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81](http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81)
You should change again your user password using the user & group window, it could be the problem.

---

### Post by makisupa123 on 2006-01-30
Probably a simpleton question....have you created the user 'userFTP'  and the associated group on your system?  (Not in proftp....in your linux system)

mak.

---

### Post by shawnzyoo on 2006-01-30
i have my user set to /bin/false
and he is in the group "userftp"
the home directory is "FTP-shared"
is this the right way?
or do i have to do something under the groups tab?
thanks for the help so far

---

### Post by shawnzyoo on 2006-01-31
bump

---

### Post by shawnzyoo on 2006-02-01
believe it or not
but i have my logins working
trial and error

my problem now is its not being forwarded correctly
[ftp://localhost](ftp://localhost)
works fine
but 
[ftp://mysite.net](ftp://mysite.net)
i get teh same login prompt
and i login and then nothing happens
any suggestions or similiar issues?

---

