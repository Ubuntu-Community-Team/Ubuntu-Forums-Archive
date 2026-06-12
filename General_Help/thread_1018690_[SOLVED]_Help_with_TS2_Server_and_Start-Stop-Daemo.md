---
title: "[SOLVED] Help with TS2 Server and Start-Stop-Daemon."
date: 2008-12-22
forum: General Help
---

### Post by XFaisalX on 2008-12-22
Hey guys, I'm new to Linux (just installed it today) and I'm having some problems.
I'm trying to install a Teamspeak Server (did all the tutorial steps until start-stop-daemon). I don't know where to get a tutorial or anything like that how to get and install start-stop-daemon, and don't even know what it does. I managed to get it somewhere but the install goes crappy =/
Also, when I was installing Teamspeak Server, I managed to come this far:

```
faisal@server-xfaisalx:~$ wget "ftp://ftp.freenet.de/pub/4players/teamspeak.org/releases/ts2_server_rc2_202319.tar.bz2"
--2008-12-22 16:33:58--  [ftp://ftp.freenet.de/pub/4players/teamspeak.org/releases/ts2_server_rc2_202319.tar.bz2](ftp://ftp.freenet.de/pub/4players/teamspeak.org/releases/ts2_server_rc2_202319.tar.bz2)
           => `ts2_server_rc2_202319.tar.bz2'
Resolving ftp.freenet.de... 194.97.2.70, 194.97.2.67, 194.97.2.68, ...
Connecting to ftp.freenet.de|194.97.2.70|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/4players/teamspeak.org/releases ... done.
==> SIZE ts2_server_rc2_202319.tar.bz2 ... 1155345
==> PASV ... done.    ==> RETR ts2_server_rc2_202319.tar.bz2 ... done.
Length: 1155345 (1.1M)

100%[======================================>] 1,155,345    820K/s   in 1.4s    

2008-12-22 16:34:00 (820 KB/s) - `ts2_server_rc2_202319.tar.bz2' saved [1155345]

faisal@server-xfaisalx:~$ user@server:~$ tar xvjf ts2_server_rc2_202319.tar.bz2
bash: user@server:~$: command not found
faisal@server-xfaisalx:~$ tar xvjf ts2_server_rc2_202319.tar.bz2
tss2_rc2/
tss2_rc2/mysql_sql/
tss2_rc2/mysql_sql/create_channel_privileges.sql
tss2_rc2/mysql_sql/create_servers.sql
tss2_rc2/mysql_sql/create_bans.sql
tss2_rc2/mysql_sql/create_channels.sql
tss2_rc2/mysql_sql/create_clients.sql
tss2_rc2/mysql_sql/create_server_privileges.sql
tss2_rc2/tcpquerydocs/
tss2_rc2/tcpquerydocs/dbuserchangeattribs.txt
tss2_rc2/tcpquerydocs/mptc.txt
tss2_rc2/tcpquerydocs/dbsuserlist.txt
tss2_rc2/tcpquerydocs/kick.txt
tss2_rc2/tcpquerydocs/banplayer.txt
tss2_rc2/tcpquerydocs/dbpi.txt
tss2_rc2/tcpquerydocs/gapl.txt
tss2_rc2/tcpquerydocs/dbuserdel.txt
tss2_rc2/tcpquerydocs/cl.txt
tss2_rc2/tcpquerydocs/pi.txt
tss2_rc2/tcpquerydocs/ci.txt
tss2_rc2/tcpquerydocs/msgu.txt
tss2_rc2/tcpquerydocs/dbsuserdel.txt
tss2_rc2/tcpquerydocs/serverset.txt
tss2_rc2/tcpquerydocs/dbci.txt
tss2_rc2/tcpquerydocs/fc.txt
tss2_rc2/tcpquerydocs/globalset.txt.bak
tss2_rc2/tcpquerydocs/dbsuserchangepw.txt
tss2_rc2/tcpquerydocs/ver.txt
tss2_rc2/tcpquerydocs/dccl.txt
tss2_rc2/tcpquerydocs/fp.txt
tss2_rc2/tcpquerydocs/dbuserid.txt
tss2_rc2/tcpquerydocs/login.txt
tss2_rc2/tcpquerydocs/banclear.txt
tss2_rc2/tcpquerydocs/lc.txt
tss2_rc2/tcpquerydocs/logmark.txt
tss2_rc2/tcpquerydocs/banlist.txt
tss2_rc2/tcpquerydocs/bandel.txt
tss2_rc2/tcpquerydocs/dbsuseradd.txt
tss2_rc2/tcpquerydocs/msg.txt
tss2_rc2/tcpquerydocs/dbfp.txt
tss2_rc2/tcpquerydocs/logfind.txt
tss2_rc2/tcpquerydocs/dbuseradd.txt
tss2_rc2/tcpquerydocs/sel.txt
tss2_rc2/tcpquerydocs/removeclient.txt
tss2_rc2/tcpquerydocs/log.txt
tss2_rc2/tcpquerydocs/globalset.txt
tss2_rc2/tcpquerydocs/banadd.txt
tss2_rc2/tcpquerydocs/sl.txt
tss2_rc2/tcpquerydocs/si.txt
tss2_rc2/tcpquerydocs/pl.txt
tss2_rc2/tcpquerydocs/dbuserlist.txt
tss2_rc2/tcpquerydocs/serverdel.txt
tss2_rc2/tcpquerydocs/ki.txt
tss2_rc2/tcpquerydocs/checkserverok.txt
tss2_rc2/tcpquerydocs/dbserverlist.txt
tss2_rc2/tcpquerydocs/dbuserchangepw.txt
tss2_rc2/tcpquerydocs/serverstart.txt
tss2_rc2/tcpquerydocs/sppriv.txt
tss2_rc2/tcpquerydocs/gi.txt
tss2_rc2/tcpquerydocs/msgall.txt
tss2_rc2/tcpquerydocs/help.txt
tss2_rc2/tcpquerydocs/serverstop.txt
tss2_rc2/tcpquerydocs/rehash.txt
tss2_rc2/tcpquerydocs/slogin.txt
tss2_rc2/tcpquerydocs/serveradd.txt
tss2_rc2/manual.html
tss2_rc2/INSTALL.mysql
tss2_rc2/README
tss2_rc2/INSTALL
tss2_rc2/Manual/
tss2_rc2/Manual/webpost2.htm
tss2_rc2/Manual/RC2servermanual-index.htm
tss2_rc2/Manual/open.gif
tss2_rc2/Manual/bandwidthandcodecs1.htm
tss2_rc2/Manual/lastnotes1.htm
tss2_rc2/Manual/teamspeak.gif
tss2_rc2/Manual/toc.css
tss2_rc2/Manual/button.gif
tss2_rc2/Manual/login.png
tss2_rc2/Manual/webpost3.htm
tss2_rc2/Manual/teamspeakrc2servermanual1.htm
tss2_rc2/Manual/RC2servermanual-css.rtf
tss2_rc2/Manual/windowsinstalling.htm
tss2_rc2/Manual/howtoruntheteamspeakserverasaserviceunderwinxpand20001.htm
tss2_rc2/Manual/logout1.htm
tss2_rc2/Manual/whatsnewinteamspeakreleasecandidate21.htm
tss2_rc2/Manual/closingdowntheserver4.htm
tss2_rc2/Manual/DocToHelp.js
tss2_rc2/Manual/frequentlyaskedquestions1.htm
tss2_rc2/Manual/installingtheserver4.htm
tss2_rc2/Manual/qilostmyserveradminpassword.htm
tss2_rc2/Manual/startingtheserver1.htm
tss2_rc2/Manual/superadminservers.png
tss2_rc2/Manual/_TeamSpeak RC2 Server manual-1.png
tss2_rc2/Manual/qwhatportsdoestheserveruse.htm
tss2_rc2/Manual/superadminstart.png
tss2_rc2/Manual/default.htm
tss2_rc2/Manual/mainconfig1.htm
tss2_rc2/Manual/linuxinstalling.htm
tss2_rc2/Manual/RC2servermanual-blank.htm
tss2_rc2/Manual/RC2servermanuallinux
tss2_rc2/Manual/requirementstoruntheteamspeak2server1.htm
tss2_rc2/Manual/licensing1.htm
tss2_rc2/Manual/miscellaneous1.htm
tss2_rc2/Manual/usermanager.png
tss2_rc2/Manual/qwhatsupportdoesteamspeakoffer.htm
tss2_rc2/Manual/webadminningtheserver1.htm
tss2_rc2/Manual/RC2servermanual-toc.htm
tss2_rc2/Manual/serversettings.png
tss2_rc2/Manual/closingdowntheserver5.htm
tss2_rc2/Manual/startinguptheserver1.htm
tss2_rc2/Manual/installingtheserver5.htm
tss2_rc2/Manual/ports1.htm
tss2_rc2/Manual/administration1.htm
tss2_rc2/Manual/back.gif
tss2_rc2/Manual/serverpermissions1.htm
tss2_rc2/Manual/loggingin1.htm
tss2_rc2/Manual/closed.gif
tss2_rc2/Manual/superadmin1.htm
tss2_rc2/Manual/yourips1.htm
tss2_rc2/Manual/C1H_HTML.css
tss2_rc2/Manual/whatistheteamspeak2server1.htm
tss2_rc2/Manual/serversettings1.htm
tss2_rc2/Manual/topic.gif
tss2_rc2/Manual/tcpqueryfunction1.htm
tss2_rc2/Manual/usermanager1.htm
tss2_rc2/server_linux
tss2_rc2/teamspeak2-server_startscript
tss2_rc2/sqlite.so
tss2_rc2/httpdocs/
tss2_rc2/httpdocs/server_manager_permission_ca.html
tss2_rc2/httpdocs/database_client_manager_add.html
tss2_rc2/httpdocs/index.html
tss2_rc2/httpdocs/choice_box.html
tss2_rc2/httpdocs/database_client_manager_clientlist.html
tss2_rc2/httpdocs/database_sclient_manager_add.html
tss2_rc2/httpdocs/help/
tss2_rc2/httpdocs/help/superadmin_manager.html
tss2_rc2/httpdocs/help/user_manager.html
tss2_rc2/httpdocs/help/server_overview.html
tss2_rc2/httpdocs/help/server_settings.html
tss2_rc2/httpdocs/help/global_settings.html
tss2_rc2/httpdocs/help/permissions_general.html
tss2_rc2/httpdocs/help/servers.html
tss2_rc2/httpdocs/database_client_manager.html
tss2_rc2/httpdocs/login_error.html
tss2_rc2/httpdocs/server_country_option.html
tss2_rc2/httpdocs/server_manager_overview.html
tss2_rc2/httpdocs/server_manager_serverlist.html
tss2_rc2/httpdocs/database_sclient_manager_edit.html
tss2_rc2/httpdocs/database_sclient_manager.html
tss2_rc2/httpdocs/database_sclient_manager_clientlist.html
tss2_rc2/httpdocs/server_manager_permissionfield.html
tss2_rc2/httpdocs/footer.html
tss2_rc2/httpdocs/login.html
tss2_rc2/httpdocs/header.html
tss2_rc2/httpdocs/server_manager_permission.html
tss2_rc2/httpdocs/slogin.html
tss2_rc2/httpdocs/ok_box.html
tss2_rc2/httpdocs/server_manager_permission_sa.html
tss2_rc2/httpdocs/server_manager_grouppermission.html
tss2_rc2/httpdocs/menu_top.html
tss2_rc2/httpdocs/server_manager_permission_u.html
tss2_rc2/httpdocs/server_manager_add.html
tss2_rc2/httpdocs/error_box.html
tss2_rc2/httpdocs/server_manager_servers.html
tss2_rc2/httpdocs/server_manager.html
tss2_rc2/httpdocs/server_manager_permission_r.html
tss2_rc2/httpdocs/server_manager_permission_op.html
tss2_rc2/httpdocs/server_manager_settings.html
tss2_rc2/httpdocs/server_manager_permission_v.html
tss2_rc2/httpdocs/menu_bottom.html
tss2_rc2/httpdocs/server_basic_settings.html
tss2_rc2/httpdocs/gfx/
tss2_rc2/httpdocs/gfx/server_settings.jpg
tss2_rc2/httpdocs/gfx/permissions.jpg
tss2_rc2/httpdocs/gfx/delete.png
tss2_rc2/httpdocs/gfx/user_icon.png
tss2_rc2/httpdocs/gfx/uhr_icon.png
tss2_rc2/httpdocs/gfx/server-stop.png
tss2_rc2/httpdocs/gfx/user_manager.jpg
tss2_rc2/httpdocs/gfx/server_overview.jpg
tss2_rc2/httpdocs/gfx/edit.png
tss2_rc2/httpdocs/gfx/add_server.png
tss2_rc2/httpdocs/gfx/headerline.gif
tss2_rc2/httpdocs/gfx/servers.jpg
tss2_rc2/httpdocs/gfx/server-run.png
tss2_rc2/httpdocs/gfx/helpnav.jpg
tss2_rc2/httpdocs/gfx/under_hl.gif
tss2_rc2/httpdocs/gfx/superadmin_manager.jpg
tss2_rc2/httpdocs/gfx/pixel.gif
tss2_rc2/httpdocs/gfx/vBulletin_logo.gif
tss2_rc2/httpdocs/gfx/helppages.png
tss2_rc2/httpdocs/gfx/add_client.png
tss2_rc2/httpdocs/gfx/server_icon.png
tss2_rc2/httpdocs/gfx/global_settings.jpg
tss2_rc2/httpdocs/gfx/help.gif
tss2_rc2/httpdocs/gfx/select.png
tss2_rc2/httpdocs/gfx/select_short.png
tss2_rc2/httpdocs/gfx/serveradminlogin.gif
tss2_rc2/httpdocs/gfx/menu_background.gif
tss2_rc2/httpdocs/gfx/helppages.jpg
tss2_rc2/httpdocs/database_client_manager_edit.html
tss2_rc2/httpdocs/server_manager_servers_list.html
tss2_rc2/sqlite_sql/
tss2_rc2/sqlite_sql/edit_channel.sql
tss2_rc2/sqlite_sql/upgrade_1.sql
tss2_rc2/sqlite_sql/delete_ban_ip.sql
tss2_rc2/sqlite_sql/edit_server_privilege.sql
tss2_rc2/sqlite_sql/read_bans.sql
tss2_rc2/sqlite_sql/read_server_port.sql
tss2_rc2/sqlite_sql/create_channel_privileges.sql
tss2_rc2/sqlite_sql/read_server.sql
tss2_rc2/sqlite_sql/create_servers.sql
tss2_rc2/sqlite_sql/remove_bans.sql
tss2_rc2/sqlite_sql/delete_channel_privilege.sql
tss2_rc2/sqlite_sql/read_servers.sql
tss2_rc2/sqlite_sql/create_nicks.sql
tss2_rc2/sqlite_sql/read_clients_name.sql
tss2_rc2/sqlite_sql/create_bans.sql
tss2_rc2/sqlite_sql/read_client_channels_privileges.sql
tss2_rc2/sqlite_sql/edit_server.sql
tss2_rc2/sqlite_sql/delete_server.sql
tss2_rc2/sqlite_sql/new_channel_privilege.sql
tss2_rc2/sqlite_sql/delete_client.sql
tss2_rc2/sqlite_sql/read_channels.sql
tss2_rc2/sqlite_sql/edit_client.sql
tss2_rc2/sqlite_sql/read_channel.sql
tss2_rc2/sqlite_sql/read_channel_privilege.sql
tss2_rc2/sqlite_sql/new_server.sql
tss2_rc2/sqlite_sql/create_channels.sql
tss2_rc2/sqlite_sql/new_channel.sql
tss2_rc2/sqlite_sql/create_settings.sql
tss2_rc2/sqlite_sql/search_client.sql
tss2_rc2/sqlite_sql/read_server_privilege.sql
tss2_rc2/sqlite_sql/read_clients.sql
tss2_rc2/sqlite_sql/delete_ban.sql
tss2_rc2/sqlite_sql/remove_moderatedattribs.sql
tss2_rc2/sqlite_sql/upgrade_2.sql
tss2_rc2/sqlite_sql/delete_channel.sql
tss2_rc2/sqlite_sql/read_channel_privileges.sql
tss2_rc2/sqlite_sql/create_clients.sql
tss2_rc2/sqlite_sql/edit_client_lastonline.sql
tss2_rc2/sqlite_sql/read_client_login.sql
tss2_rc2/sqlite_sql/upgrade_3.sql
tss2_rc2/sqlite_sql/create_server_privileges.sql
tss2_rc2/sqlite_sql/edit_channel_privilege.sql
tss2_rc2/sqlite_sql/new_client.sql
tss2_rc2/sqlite_sql/new_server_privilege.sql
tss2_rc2/sqlite_sql/read_active_servers.sql
tss2_rc2/sqlite_sql/new_ban.sql
tss2_rc2/sqlite_sql/read_clients_id.sql
tss2_rc2/libsqlmy.so
tss2_rc2/LICENSE
faisal@server-xfaisalx:~$ sudo mv tss2_rc2/ /opt
[sudo] password for faisal: 
faisal@server-xfaisalx:~$ sudo adduser teamspeak
Adding user `teamspeak' ...
Adding new group `teamspeak' (1001) ...
Adding new user `teamspeak' (1001) with group `teamspeak' ...
Creating home directory `/home/teamspeak' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for teamspeak
Enter the new value, or press ENTER for the default
	Full Name []: Teamspeak Daemon Runner
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
faisal@server-xfaisalx:~$ sudo chown teamspeak /opt/tss2_rc2
faisal@server-xfaisalx:~$ sudo usermod -s /bin/false teamspeak
faisal@server-xfaisalx:~$ ls -la /opt/tss2_rc2/
total 1492
drwxr-xr-x 7 teamspeak faisal   4096 2007-08-02 19:57 .
drwxr-xr-x 3 root      root     4096 2008-12-22 16:35 ..
drwxr-xr-x 4 faisal    faisal   4096 2007-08-02 19:57 httpdocs
-rw-r--r-- 1 faisal    faisal   2601 2007-08-02 14:07 INSTALL
-rw-r--r-- 1 faisal    faisal   3083 2007-08-02 13:38 INSTALL.mysql
-rw-r--r-- 1 faisal    faisal 234289 2004-03-09 13:40 libsqlmy.so
-rw-r--r-- 1 faisal    faisal  20507 2007-08-02 13:38 LICENSE
drwxr-xr-x 2 faisal    faisal   4096 2004-03-09 13:41 Manual
-rw-r--r-- 1 faisal    faisal    353 2004-03-09 13:40 manual.html
drwx------ 2 faisal    faisal   4096 2007-08-02 13:25 mysql_sql
-rw-r--r-- 1 faisal    faisal   3964 2007-08-02 13:49 README
-rwxr--r-- 1 faisal    faisal 948232 2007-08-02 13:50 server_linux
-rw-r--r-- 1 faisal    faisal 251908 2004-03-09 13:40 sqlite.so
drwx------ 2 faisal    faisal   4096 2007-08-02 13:25 sqlite_sql
drwxr-xr-x 2 faisal    faisal   4096 2004-03-09 13:42 tcpquerydocs
-rwxr-xr-x 1 faisal    faisal   2465 2004-03-09 13:40 teamspeak2-server_startscript
faisal@server-xfaisalx:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:113:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:118::/home/saned:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
polkituser:x:109:120:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:121:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false
faisal:x:1000:1000:Faisal,,,:/home/faisal:/bin/bash
teamspeak-server:x:112:126::/var/lib/teamspeak-server:/bin/false
teamspeak:x:1001:1001:Teamspeak Daemon Runner,,,:/home/teamspeak:/bin/false
faisal@server-xfaisalx:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
faisal@server-xfaisalx:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
[sudo] password for faisal: 
Sorry, try again.
[sudo] password for faisal: 
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
faisal@server-xfaisalx:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)

```

Can anyone help me fix this problem ASAP?
Help would greatly be appreciated =)

---

### Post by redilyn on 2008-12-22
I've quickly looked over the tutorial and the output you posted. Here is what I notice:

The file mysql_sql is supposed to have execute permissions, yours does not.

The file server_linux is supposed to have execute permissions, yours does not.

The file sqlite_sql is supposed to have execute permissions, yours does not.

Try this:

```

sudo chmod +X /opt/tss2_rc2/mysql_sql
sudo chmod +X /opt/tss2_rc2/server_linux
sudo chmod +X /opt/tss2_rc2/sqlite_sql 

```

Then

```

sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux

```

---

### Post by XFaisalX on 2008-12-22
Okay I'm gonna try it in a second, thank you very much for the help =D

---

### Post by XFaisalX on 2008-12-22
Okay, I typed it in but got an error, and I got no other terminal instances running:

```
faisal@server-xfaisalx:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
[sudo] password for faisal: 
Error, Either an old instance of teamspeak is still running, or
       an other application is using the tcpquery port!
Error, Server was not started!
faisal@server-xfaisalx:~$ 

```

Help?

---

### Post by redilyn on 2008-12-22
okay, check to see if teamspeak is already running

Type the following in terminal:
```

ps aux

```

Look for teamspeak or teamspeak server and let me know what you find.

I think you should see /opt/tss2_rc2/server_linux

---

### Post by XFaisalX on 2008-12-22
This is what I get:

112       4875  1.2  0.1  62760  1748 ?        SNl  19:27   0:01 /usr/lib/teamsp

That's the only thing that is related as Teamspeak.
Now how do I close it?
Cuz I don't see anything in the taskbar, and I don't know if there is some special program like Task Manager =S
(Sorry I'm really new with this.)

---

### Post by redilyn on 2008-12-22
Okay, if you have gnome installed click System -> Adminstration -> System monitor

Click on the processes tab, Look here you should find teamspeak.

You can kill it from here if you like.

I'm not sure if you need too though. You might be able to continue with the tutorial now since teamspeak is already running.

Try connecting to the teamspeak server http://<server_ip>:14534

---

### Post by redilyn on 2008-12-22
I should also mention that the newest versions of teamspeak server and client are included in the Ubuntu repo's if you are using 8.10 (Intrepid) :)

```

sudo apt-get install teamspeak-server teamspeak-client

```

If you are going to go this route (might be a good idea) be sure to remove the TS files you have now

```

sudo rm -R /opt/tss2_rc2/

```

---

### Post by XFaisalX on 2008-12-22
Well I killed the process even though it was still sleeping, and now it says this:
```
faisal@server-xfaisalx:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
TeamSpeak Server Daemon started with PID 6364
faisal@server-xfaisalx:~$ 
faisal@server-xfaisalx:~$ 
faisal@server-xfaisalx:~$ 
faisal@server-xfaisalx:~$ 

```
Also when I try to connect with either ts or to the Server Panel, it does not connect =/
It also doesn't show in the processes.
What now =/?

---

### Post by redilyn on 2008-12-22
Alright.

Double check to make sure teamspeak is running

Click System -> Adminstration -> System Monitor

Click on the Processes Tab

Click view and choose all processes

Look for teamspeak or server_linux, if you can not find it, Look in the ID column for 6364 (if you have not restarted the server since your last post).

If you do not find teamspeak it is time to try and restart it

```

sudo killall server_linux
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux

```

Try to connect again

--------------------------------------------

If you do find teamspeak then the next step is to resolve the connection problem.

Double check the server ip

```

ifconfig

```

Look for eth0 and then write down the ip address

```

eth0      Link encap:Ethernet  HWaddr 00:11:43:2f:c1:31  
          [COLOR="DarkRed"]inet addr:10.1.0.62[/COLOR]  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::211:43ff:fe2f:c131/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27293839 (27.2 MB)  TX bytes:4091535 (4.0 MB)
          Interrupt:16 

```

Try to connect with ip.

If it does not work, time to check the firewall:

```

sudo ufw status
[/code[

If its enabled/loaded, disable it for the time being

[code]
sudo ufw disable

```

Try to connect to the server again.

Let me know how you make out

---

### Post by XFaisalX on 2008-12-22
Ty I am able to connect to it =D
Thanks for all the help m8 ^^
Now I'm gonna ask some ppl to join, and I'll tell ya how it works out.
Thanks a lot for the help.

---

### Post by redilyn on 2008-12-22
Your welcome, What did you have to do to get it working??

You should make this post as solved.

Merry Christmas :)

---

### Post by XFaisalX on 2008-12-22
It was probably that I had to put in local Ip, and give other people my External Ip. That was most likely the cause (stupid action of me xD, oh well we all learn)
Thanks for all the help m8, now I've learnt a bit more of Linux =D
Merry Christmas ^^

---

