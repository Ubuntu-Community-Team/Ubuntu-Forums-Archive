---
title: "Pure-ftpd + pureadmin (Ftp server with gui) HOWTO"
date: 2005-11-16
forum: Desktop Environments
---

### Post by suoko on 2005-11-16
These are all steps to follow in order to have a nice ftp server with an easy gui.

1) install attached pureadmin deb file
2) Comment the line in /etc/inetd.conf containing 'ftp'
3) Open /etc/default/pure-ftpd-common and change STANDALONE_OR_INETD=inetd to
STANDALONE_OR_INETD=standalone
4) run 'groupadd ftpgroup' and
'useradd -g ftpgroup -d /dev/null -s /etc ftpuser'
5) create ftpuser directory 'sudo mkdir /home/ftpusers'
6) create joe user directory 'sudo mkdir /home/ftpusers/joe' (you can create a directory for each ftp user)
7) run 'sudo pure-pw useradd joe -u ftpuser -d /home/ftpusers/joe' (a)
8 ) run 'sudo pure-pw mkdb'
9) run 'sudo ln -s /etc/pure-ftpd/pureftpd.passwd /etc/pureftpd.passwd'
10) run 'sudo ln -s /etc/pure-ftpd/pureftpd.pdb /etc/pureftpd.pdb'
11) run 'sudo ln -s /etc/pure-ftpd/conf/PureDB
/etc/pure-ftpd/auth/PureDB'
12) Create file /etc/pure-ftpd/conf/UnixAuthentication containing only the string 'no' without quotes. (c)
13) Modify permissions of /home/ftpusers directory (b) and of any subdirectories. Owner must be ftpuser while Group must be ftpgroup 
14) run sudo pureadmin.
15) stop firestarter if installed
16) through "menu editor" modify pureadmin entry command (under 'system tools') from 'pureadmin' to 'gksudo pureadmin'

NOTES
(a) joe will be your test user. You can change user joe and/or add other users through pureadmin
(b) Easy way to change permissions: run 'sudo nautilus', go to /home, change owner with ftpuser and group with ftpgroup. Tick special flags 'set user ID' and 'set group ID'. [not sure if this ticks are necessary]
(c) run 'sudo echo no > cat >/etc/pure-ftpd/conf/UnixAuthentication'

Be aware that pureadmin must be run as root.

---

### Post by Kyral on 2005-11-16
Suggest be moved to the Customizations/Tips & Tricks Forum

---

### Post by basketcase on 2005-11-16
Thanks!!  Can't wait to get home and try it out!

---

### Post by Rumor on 2005-11-30
[QUOTE=suoko]These are all steps to follow in order to have a nice ftp server with an easy gui.
[/QUOTE]

Worked like a charm, thanks!

---

### Post by maxter on 2005-12-22
the above howto does not enable the start/stop menu in the 'pureftpd' menu.
for a full working configuration of pureadmin it should be also added another symbolic link with the following instruction:

```

sudo mkdir /etc/rc.d
sudo ln - s /etc/init.d/pure-ftpd /etc/rc.d/rc.pure-ftpd

```

eventually restart pureadmin and the start/stop server menu will now works

---

### Post by Gerbils on 2006-06-21
"package architecture (i386) does not match system (amd64)"
Is there a package available for AMD64 users as well?

---

### Post by tcollogne on 2006-07-11
I just can't get it to work. Using this guide I can login as an os user, but not as a virtual user created in pure-ftpd.

Any ideas?

---

### Post by zir0n on 2006-07-12
i'm having the same problem as tcollogne, i'm able to log into the ftp server with normal user accounts, but not the ones created in the pureadmin program

:-k

---

### Post by Boomy on 2006-07-14
Same here and it logs me into the root directory. :confused:

---

### Post by ... on 2006-07-23
OK guys, this howto didn't work for me...  What did is:

1. find the pure-admin pacakge in the ubuntu repositories.  I am not sure if it is in the ones that come with ubuntu, but the one that are in the automatix source.list has it. **Do not use the one linked at the top of the page, it was complied incorrectly and does not support any of the logfile viewer options, or seeing the active transfers**

2. run **sudo apt-get install pureadmin**
3. create group ftpgroup **sudo groupadd ftpgroup** 
4. create user ftp user **sudo useradd -g ftpgroup -d /dev/null -s /etc ftpuser **
5. create ftpuser directory **sudo mkdir /home/ftpusers** 
6. create joe user directory **sudo mkdir /home/ftpusers/joe** (you can create a directory for each ftp user) 
7. create virtual user joe **sudo pure-pw useradd joe -u ftpuser -d /home/ftpusers/joe**
8. update virtual user db **sudo pure-pw mkdb**
9. run **sudo gedit /etc/pure-ftp/conf/AnonymousOnly** and in the window that comes up type "no" without the quotes, and save
10. run **sudo gedit /etc/pure-ftp/conf/NoAnonymous** and in the window that come up type "yes" without the quotes
11. run **sudo gedit /etc/pure-ftp/conf/PureDB** and in the window that comes up type "/etc/pure-ftpd/pureftpd.pdb" without the quotes
12. run **sudo gedit /etc/pure-ftp/conf/PAMAuthentication** and in the window that comes up type "yes" in qotes if you want sytem users to be able to login (ie the users that can login with) or to "no" if you want only the virtual users created in pureadmin.  The latter reduces up the time that pure-ftpd takes to reject users that aren't allowed to login...
13. run **sudo gedit /etc/pure-ftp/conf/CreateHomeDir** and in the window that comes up type "yes" without the quotes.
14. run **sudo chown -R ftpuser:ftpgroup /home/ftpusers** 
15. run **sudo pureadmin**
16. go to edit->prefrences->external at the top.  
17. click the big 'search' button in the middle.  The password and pdb box should become /etc/pure-ftpd/pureftpd.passwd and /etc/pure-ftpd/pureftpd.pdb (if they don't change them accordingly)
18. close out of that and add a user...
19. hold your breath and pray that it worked :P

Steps 5-8 shouldn't be needed, but I think that they create some important files (etc/pure-ftpd/pureftpd.passwd and /etc/pure-ftpd/pureftpd.pdb), so it can't hurt to do them...  

I hope I didn't make any typos, although it is about 10pm here...  I am going to be on vacation for about a week, so I won't be able to help until early august](*,)

GOOD LUCK!

---

### Post by b3nw on 2007-10-04
Just figured would point out conf options because their horribly not documented.


                        'AllowAnonymousFXP' => ['-W'],
                        'AllowDotFiles' => ['-z'],
                        'AllowUserFXP' => ['-w'],
                        'AltLog' => ['-O %s', \&parse_string],
                        'AnonymousBandwidth' => ['-t %s', \&parse_number_1_2],
                        'AnonymousCanCreateDirs' => ['-M'],
                        'AnonymousCantUpload' => ['-i'],
                        'AnonymousOnly', => ['-e'],
                        'AnonymousRatio' => ['-q %d:%d', \&parse_number_2],
                        'AntiWarez' => ['-s'],
                        'AutoRename' => ['-r'],
                        'Bind' => ['-S %s', \&parse_string],
                        'BrokenClientsCompatibility' => ['-b'],
                        'CallUploadScript' => ['-o'],
                        'ChrootEveryone' => ['-A'],
                        'CreateHomeDir' => ['-j'],
                        'CustomerProof' => ['-Z'],
                        'Daemonize' => ['-B'],
                        'DisplayDotFiles' => ['-D'],
                        'DontResolve' => ['-H'],
                        'ForcePassiveIP' => ['-P %s', \&parse_string],
                        'FortunesFile' => ['-F %s', \&parse_filename],
                        'IPV4Only' => ['-4'],
                        'IPV6Only' => ['-6'],
                        'KeepAllFiles' => ['-K'],
                        'LimitRecursion' => ['-L %d:%d', \&parse_number_2],
                        'LogPID' => ['-1'],
                        'MaxClientsNumber' => ['-c %d', \&parse_number_1],
                        'MaxClientsPerIP' => ['-C %d', \&parse_number_1],
                        'MaxDiskUsage' => ['-k %d', \&parse_number_1],
                        'MaxIdleTime' => ['-I %d', \&parse_number_1],
                        'MaxLoad' => ['-m %d', \&parse_number_1],
                        'MinUID' => ['-u %d', \&parse_number_1],
                        'NATmode' => ['-N'],
                        'NoAnonymous' => ['-E'],
                        'NoChmod' => ['-R'],
                        'NoRename' => ['-G'],
                       'PassivePortRange' => ['-p %d:%d', \&parse_number_2],
                        'PerUserLimits' => ['-y %d:%d', \&parse_number_2],
                        'ProhibitDotFilesRead' => ['-X'],
                        'ProhibitDotFilesWrite' => ['-x'],
                        'Quota' => ['-n %d:%d', \&parse_number_2],
                        'SyslogFacility' => ['-f %s', \&parse_word, 99],
                        'TLS' => ['-Y %d', \&parse_number_1],
                        'TrustedGID' => ['-a %d', \&parse_number_1],
                        'TrustedIP' => ['-V %s', \&parse_ip],
                        'Umask' => ['-U %s:%s', \&parse_umask],
                        'UserBandwidth' => ['-T %s', \&parse_number_1_2],
                        'UserRatio' => ['-Q %d:%d', \&parse_number_2],
                        'VerboseLog' => ['-d'],
                        'FsCharset' => ['-8 %s', \&parse_string],
                        'ClientCharset' => ['-9 %s', \&parse_string],
                    );

my %authconf = ('ExtAuth' => ['extauth:%s', \&parse_sockname],
                                'LDAPConfigFile' => ['ldap:%s', \&parse_filename, 0,
                                                                                 'ldap'],
                                'MySQLConfigFile' => ['mysql:%s', \&parse_filename, 0,
                                                                          'mysql'],
                                'PGSQLConfigFile' => ['pgsql:%s', \&parse_filename, 0,
                                                                          'postgresql'],
                                'PAMAuthentication' => ['pam'],
                                'PureDB' => ['puredb:%s', \&parse_filename],
                                'UnixAuthentication' => ['unix'],
                           );

# examine all configuration files in /etc/pure-ftpd/conf

---

### Post by andale on 2008-01-14
don't guess there's a more up-to-date version of this, the first file it tells me to open is blank, so i stopped.

---

### Post by ramboza on 2008-06-17
Same problem, virtual user accounts won't work. Local accounts bring to root directory when logged in...

---

### Post by tmetzcc325 on 2008-07-18
So I am having this problem.  When I was on 7.10, I had installed pureftp and set it up according to this how-to that is laid out at the beginning of this thread, and everything worked well.

When Hardy came out, I did a clean install, and reinstalled pureftp, but did not follow any of the steps to create the virtual users.  At this time, it was possible for me to connect to the server at home from work and log in using my local credentials ( not smart, I know, but not too concerned about it).  Just now, I followed this guide again to set up the virtual users, just like in the past.  Now, however, when I attempt to ftp into the computer from work, it won't even give me the option to login.  After a minute or so, I just get 'connection closed by remote host'.

Do these instructions still work for Hardy?  I have done them a few times, so I know I didn't mistype anything, but now I can't ftp in at all.

Any ideas?

---

