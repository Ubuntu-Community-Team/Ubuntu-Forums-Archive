---
title: "NXclient NXserver connection error"
date: 2009-01-07
forum: General Help
---

### Post by briztian on 2009-01-07
I have read many threads and have done a few fixes but am still unable to connect through the NXclient from XP to my Ubuntu 8.10 laptop. 

Background: 

-I'm connecting from XP to Ubuntu
-All ports are set up for port 22 and fowarded correctly.
-I can successfully log in to Ubuntu from XP with PuTTy.
-I have never had a successfull session.
-I get the same error if i try logging in from work or from another computer at home through LAN.

Error message reads
```
NX> 203 NXSSH running with pid: 11580
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 98.150.39.135 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: briztian
NX> 102 Password: ********
NX> 103 Welcome to: BTA-Mobile1 user: briztian
NX> 105 Listsession --user="briztian" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: briztian
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="bta\040test" --type="unix-gnome" --geometry="1600x1079" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1600x1079x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 08B0E83F. To get detailed information about
NX> 595 ERROR: the error search for the string 08B0E83F in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

```

It looks to me like an authorization issue.

Any ideas?

---

### Post by Titan8990 on 2009-01-07
Try doing what the error tells you....


cat /var/log/messages | grep 08B0E83F

---

### Post by briztian on 2009-01-07
Let me first thank you for helping.

I've mauled over the message log but can't determine the correct route to take.

I work in IT with programmers who also use Ubuntu and they can't figure it out either. I know it's not my ports because ssh works.

I used the command you gave me and it reads:

```
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 ERROR: NXNODE Ver. 3.3.0-3  (Error id eD452A8)
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 ERROR: create session: run commands
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 ERROR: execution of last command failed
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/briztian/.nx/C-BTA-Mobile1-1004-E759C16BEA1DC4912BFAA895BB538A87/scripts/authority'
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 exit value: 1
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 stdout:
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 stderr: xauth:  /home/briztian/.Xauthority not writable, changes will be ignored
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 init: stdin arguments: user=briztian,userip=66%2e162%2e146%2e82,uniqueid=E759C16BEA1DC4912BFAA895BB538A87,display=1004,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e12,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=bta%20test,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1600x1079x32%2brender,keyboard=pc102%2fen_US,geometry=1600x1079,link=adsl
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NXNodeExec::exec('startsession', 'user=briztian&userip=66%2e162%2e146%2e82&uniqueid=E759C16BEA1DC4...', 'localhost', 22) called at handlers/nxserver.pl line 3461
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NXShell::handler_session_start('--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 373
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --encryption="1" --cache="16M" ...') called at NXShell.pm line 145
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NXShell::run() called at nxserver.pl line 4463
Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) eval {...} called at nxserver.pl line 4422

```

This is from the message log.

The NXclient connects, authenticates, and begins downloading the session before it errors out.

---

### Post by Titan8990 on 2009-01-07
Here:

Jan  7 08:54:03 BTA-Mobile1 NXSERVER-3.3.0-8[25963]: ERROR: (exception id 08B0E83F) NX> 596 stderr: xauth:  /home/briztian/.Xauthority not writable, changes will be ignored


it looks like the NXserver daemon does not have permission to write to a directory it needs to. This may not actually be a part of the problem but I personally would start by looking at the permissions of this directory and others that the NXserver needs to operate.

---

### Post by briztian on 2009-01-07
Is there a way to change the permissions for that file or change the permissions for NXserver to run as administrator every time in order to write to that file?

---

### Post by briztian on 2009-01-09
I removed all existence of NX and purged all directories and reinstalled with the guide and have the same problem.

Any ideas?

---

### Post by commonplace on 2009-01-24
Here's how I resolved my similar (if not identical) issue.

From the terminal on the server, in your home directory (/home/<username>):

```

cd .nx
mv cache-gnome/ cache-gnome.old/
mv cache-unix-gnome/ cache-unix-gnome.old/
mv temp/ temp.old/
sudo /etc/init.d/nxserver restart
```


All that's doing is renaming the cache-gnome, cache-unix-gnome, and temp directories. You *could* just delete them, but I rarely delete something unless I'm absolutely certain of the consequences. They appear safe to delete, and I can't really imagine what would be in there -- the only one that I didn't rename was the 'config' folder, which has the configuration (no surprise there).

So I'd say it's worth a shot! :)  Fixed my problem.

/Kevin

---

### Post by alexstup on 2010-02-05
.Xauthority not writable because this file already used in your current gnome or kde session. logout from X or add another user.

---

