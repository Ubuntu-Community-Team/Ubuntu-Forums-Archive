---
title: "exporting display from su (mythtv) to GDE/X11?"
date: 2006-12-17
forum: Desktop Environments
---

### Post by oneiromancer on 2006-12-17
OK guys, it's uber-noob time...  
This is my first time resorting to posting a whole new thread (though I pretty much took over one in Multimedia & Video forum, with much help from Gerick), so go easy on me...  I used to export my displays from the lab to my dorm PC back in college, but that was on Redhat, and I think some XServer software for windows, and also it was 6 years ago....  

What I want to do now *seems* simpler, and I've already gotten rid of the tcp nolisten part of my xserverrc file (maybe not necessary, but plan to use later for logging in from upstairs computer), but can't seem to get gui apps to open as a superuser...  is there a different way, and putting that aside, whats the right way to export displays in ubuntu?  Purpose in this case is to su to user mythtv and reconfigure mythtv there through mythtv-setup*. 

Only posts I found suggested something like export DISPLAY=localhost:0.0, and it was two posts saying that it didnt work (one reported the astonishing fact that substituting 127.0.0.1 for localhost made *NO* difference, can you imagine that?  Surely that was the fix I needed, replacing a term with a completely interchangeable substitute, but no... :-} See, even noobs can pick on other noobs if they feel like it...)

[SIZE="1"]*for those interested: I'm trying to change tuner card config, and it has to be done from mythtv user, or at least I don't trust it done from my account because when I first was getting mythtv setup, I got stuck on this for a while because I couldn't log into mythtv from GDE until I looked back at Dapper myth guide, as edgy one left out step for enabling login on mythtv user...  and now I'm having problems logging in as mythtv from GDE login again, though I was ablle to until this last reboo... I started having weird errors I couldn't read exclusively when changing between my account and mythtv, and it changed to something different in a different box  I also can't read after a restart, only before if I escaped the error message login worked, now escaping it or selecting ok fail to log me into mythtv user account....  very confusing, but a subject for a different post I suspect)[/SIZE]

---

### Post by superm1 on 2006-12-17
> **oneiromancer said:**
> OK guys, it's uber-noob time...  
This is my first time resorting to posting a whole new thread (though I pretty much took over one in Multimedia & Video forum, with much help from Gerick), so go easy on me...  I used to export my displays from the lab to my dorm PC back in college, but that was on Redhat, and I think some XServer software for windows, and also it was 6 years ago....  

What I want to do now *seems* simpler, and I've already gotten rid of the tcp nolisten part of my xserverrc file (maybe not necessary, but plan to use later for logging in from upstairs computer), but can't seem to get gui apps to open as a superuser...  is there a different way, and putting that aside, whats the right way to export displays in ubuntu?  Purpose in this case is to su to user mythtv and reconfigure mythtv there through mythtv-setup*. 

Only posts I found suggested something like export DISPLAY=localhost:0.0, and it was two posts saying that it didnt work (one reported the astonishing fact that substituting 127.0.0.1 for localhost made *NO* difference, can you imagine that?  Surely that was the fix I needed, replacing a term with a completely interchangeable substitute, but no... :-} See, even noobs can pick on other noobs if they feel like it...)

[SIZE=1]*for those interested: I'm trying to change tuner card config, and it has to be done from mythtv user, or at least I don't trust it done from my account because when I first was getting mythtv setup, I got stuck on this for a while because I couldn't log into mythtv from GDE until I looked back at Dapper myth guide, as edgy one left out step for enabling login on mythtv user...  and now I'm having problems logging in as mythtv from GDE login again, though I was ablle to until this last reboo... I started having weird errors I couldn't read exclusively when changing between my account and mythtv, and it changed to something different in a different box  I also can't read after a restart, only before if I escaped the error message login worked, now escaping it or selecting ok fail to log me into mythtv user account....  very confusing, but a subject for a different post I suspect)[/SIZE]
Well if this is on a local machine, there is no need for exporting displays to run apps as superuser.  Your primary user account should have wheel rights, allowing it to use sudo.

just ```
sudo mythtv-setup
``` would start it.

If this is on a remote machine, your best bet is to forward X over SSH.  So ssh into the box you are running mythtv-setup from by ```
ssh user@machine -X
```

---

### Post by oneiromancer on 2006-12-17
> Well if this is on a local machine, there is no need for exporting displays to run apps as superuser. Your primary user account should have wheel rights, allowing it to use sudo.

This is true, however my goal here is not to run setup as root, but to run it as mythtv*, and while running as root would certainly allow it access to everything, I'm concerned it might screw up permissions of any files etc it creates, not allowing it to modify them or whatnot later, as I think the backend is always run under the user mythtv.  Also, how do I enable ssh logins in ubuntu?  or rlogin or any alternatives?  I think I enabled remote desktop, but it seems like I'd need to be running ubuntu upstairs to use that.  I have putty as well as Hummingbird I use for work to loging to linux there, it seems like the natural thing to use for logging in downstairs, but all the connections are refused.  

[SIZE="1"]* Who, incidentally, does not have "wheel rights", a new term to me, presumably indicating prescence on the sudoers list...  I wanted to add rights using accounts control panel, but mythtv doesn't show up there, and I looked at adding directly to sudoers list, but my main account isn't listed explicitly there, making me hesitant to do it that way[/SIZE]

---

### Post by superm1 on 2006-12-17
> **oneiromancer said:**
> This is true, however my goal here is not to run setup as root, but to run it as mythtv*, and while running as root would certainly allow it access to everything, I'm concerned it might screw up permissions of any files etc it creates, not allowing it to modify them or whatnot later, as I think the backend is always run under the user mythtv.  Also, how do I enable ssh logins in ubuntu?  or rlogin or any alternatives?  I think I enabled remote desktop, but it seems like I'd need to be running ubuntu upstairs to use that.  I have putty as well as Hummingbird I use for work to loging to linux there, it seems like the natural thing to use for logging in downstairs, but all the connections are refused.  

[SIZE=1]* Who, incidentally, does not have "wheel rights", a new term to me, presumably indicating prescence on the sudoers list...  I wanted to add rights using accounts control panel, but mythtv doesn't show up there, and I looked at adding directly to sudoers list, but my main account isn't listed explicitly there, making me hesitant to do it that way[/SIZE]

Well for a little information about the 'mythtv' user.  I work on the package for it, and it is created as a user that has a uid <1000.  This makes it a user that you typically won't login to, and a lot of things that show the 'users' on the system won't display it.  If you were to run mythtv-setup as root, the only affected things would possibly be ~/.mythtv/mysql.txt.   

Now  a little background about this file.  When you start mythtv-backend's init script, it is started as the mythtv user.  The first place it will look is /home/mythtv/.mythtv/mysql.txt for information about where the mysql server is.  If it can't contact the server from this information (or this info doesn't exist), it will look in /etc/mythtv/mysql.txt.  If it can't contact from this information, it dies.

Now for **any** user running the frontend: The first place that is checked is ~/.mythtv/mysql.txt.  If it can't make sense of this file because of permissions or unaccessible mysql server it continues on.  Next it checks if you are in the 'mythtv' group.  If you are, it will attempt to read /etc/mythtv/mysql.txt. If it can't read this file, then it will bomb out.

So......... in short:
If you run mythtv-setup as root, the worst thing that will happen is a ~/.mythtv/mysql.txt is created.  You can change the permissions of this file (or even remove the file since it's recreated when mythtv's frontend is ran).

---

### Post by oneiromancer on 2006-12-18
Arghhhh!!!!   no its not national talk like a pirate day...  I'm just incredibly frustrated because, well...  no offense, and I'm sure its not really your fault, but I trusted you...  and ran mythtv-setup as root...  and then myth suddenly no longer had any guide data, despite status showing lots left....  and so I tried removing ~/.mythtv/mysql.txt, and now it goes back to like very basic setup (choose language screen) on each launch of myth, and after selecting a language etc, it seems to quit, and if I launch again, it goes back to it again....  I'm so completely confused...  I spent too much of like 3 days getting myth working, and I have  no idea whats wrong now...  I just wanted to try and get QAM working again so as not to have unsightly antenna and reception issues, but  I'm not getting locks in QAM, and now I have no ATSC data or any data at all...  Help?  I'm not even sure where to start, but....  well, you tell me what you need to know and if this all makes sense to you...

---

### Post by superm1 on 2006-12-18
> **oneiromancer said:**
> Arghhhh!!!!   no its not national talk like a pirate day...  I'm just incredibly frustrated because, well...  no offense, and I'm sure its not really your fault, but I trusted you...  and ran mythtv-setup as root...  and then myth suddenly no longer had any guide data, despite status showing lots left....  and so I tried removing ~/.mythtv/mysql.txt, and now it goes back to like very basic setup (choose language screen) on each launch of myth, and after selecting a language etc, it seems to quit, and if I launch again, it goes back to it again....  I'm so completely confused...  I spent too much of like 3 days getting myth working, and I have  no idea whats wrong now...  I just wanted to try and get QAM working again so as not to have unsightly antenna and reception issues, but  I'm not getting locks in QAM, and now I have no ATSC data or any data at all...  Help?  I'm not even sure where to start, but....  well, you tell me what you need to know and if this all makes sense to you...
Hmm, well no guide data certainly wouldn't happen from running mythtv-setup as root.  As long as you have your sources still setup straight though, you can refresh guide data by the command indicated at the end of mythtv-setup

```
sudo /etc/cron.daily/mythtv-backend
```

If you are trying to get guide data directly from QAM - that's your troubles.  Unlike OTA, you won't be gathering the data directly.  You need to go to data direct, make an account and put the data in ahead of time.

---

### Post by oneiromancer on 2006-12-18
No, I ran /etc/cron.daily/mythfilldatabase (EDIT: ok, I forget now if I ran filldatabase, cron.daily/mythtv-backend, or both...  I think possibly both, but at what times and in what order I can't swear to... bedtime for me right now), thinking maybe it had data for ATSC OTA and cable but not for QAM, but it didnt help, now I've put it back in ATSC and I can tune channels (or could before, when I could get into myth) but had no guide data...

I'm not entirely sure what you mean about "won't be gathering the data directly", I do have zap2it account setup and it indicated updates are successful....  my main user (oneiros) had a mysql.txt file in ~/.mythtv but the mythtv user apparently didn't, and the file in /etc/mythtv/mysql.txt indicated correct mythconverg database etc, but the one (before I deleted it) in ~/.mythtv/ didnt, it had a lot of commented out text mostly, I considered copying the /etc/mythtv/mysql.txdt file into ~/.mythtv/, for one or both users...  would that work? Can you think of any reason why guide data would appear as missing from switching source to QAM and then back to ATSC?  Also, any tips for getting channel locks in QAM?  It worked on a QAM HDTV tuner I had hooked up, and I think I even got it working on this video card in windows and/or on myth at one point, but I'm not sure at what quality etc...  I think I straightened out some HW/IRQ conflicts by moving capture card to different PCI slot, and performance improved a lot in windows for ATSC capture, so I thought I'd try QAM again, but....  <shrug>  Myth's scan didnt work and neither did using DVB scan utility on standard US cable frequencies or HRC-high...  One possible source of confusion is a lack of clarity on which coax jack on ATSC 110  to hook up cable to for QAM reception, I think its same as for ATSC as I think thats the digital input and other one is analog only, but despite strong signals and decent SnR's, it never got a lock....  appreciate attempts to help...

---

### Post by superm1 on 2006-12-18
> **oneiromancer said:**
> No, I ran /etc/cron.daily/mythfilldatabase (EDIT: ok, I forget now if I ran filldatabase, cron.daily/mythtv-backend, or both...  I think possibly both, but at what times and in what order I can't swear to... bedtime for me right now), thinking maybe it had data for ATSC OTA and cable but not for QAM, but it didnt help, now I've put it back in ATSC and I can tune channels (or could before, when I could get into myth) but had no guide data...

I'm not entirely sure what you mean about "won't be gathering the data directly", I do have zap2it account setup and it indicated updates are successful....  my main user (oneiros) had a mysql.txt file in ~/.mythtv but the mythtv user apparently didn't, and the file in /etc/mythtv/mysql.txt indicated correct mythconverg database etc, but the one (before I deleted it) in ~/.mythtv/ didnt, it had a lot of commented out text mostly, I considered copying the /etc/mythtv/mysql.txdt file into ~/.mythtv/, for one or both users...  would that work? Can you think of any reason why guide data would appear as missing from switching source to QAM and then back to ATSC?  Also, any tips for getting channel locks in QAM?  It worked on a QAM HDTV tuner I had hooked up, and I think I even got it working on this video card in windows and/or on myth at one point, but I'm not sure at what quality etc...  I think I straightened out some HW/IRQ conflicts by moving capture card to different PCI slot, and performance improved a lot in windows for ATSC capture, so I thought I'd try QAM again, but....  <shrug>  Myth's scan didnt work and neither did using DVB scan utility on standard US cable frequencies or HRC-high...  One possible source of confusion is a lack of clarity on which coax jack on ATSC 110  to hook up cable to for QAM reception, I think its same as for ATSC as I think thats the digital input and other one is analog only, but despite strong signals and decent SnR's, it never got a lock....  appreciate attempts to help...

Copying the mysql.txt back and forth will work perfectly.  Like I said, all it does it points to where the mysql server is.  I've had very funky things happen to me too when messing around with the sources for my card like guide data dissappearing.  My solution was to just wipe the data source, add it again and refill the database and it came back.

As for advice about a QAM lock, can't provide too much.  Mine has always worked out of the box, now in three different states.

---

### Post by oneiromancer on 2006-12-18
OK, so copying the mysql.txt back at least fixed the starting up in mythwelcome problem, but it still had no channels, so I went and removed all the cards and sources and added them back in...  even got QAM working (I'd forgotten that TOP antenna is digital OTA ATSC, bottom one is analog/QAM, page for my card on mythtv.com reminded me), or in any case got the channels added back (trying to remember if myth has a problem handling QAM and ATSC on same card at the same time?  Or maybe just on my card, the KWorld ATSC 110?)...  but I'm getting errors trying to run cron.daily/mythtv-backend (even as root, and when not run as root it prompts me for password itself, but still gets errors...  here's a paste:
oneiros@Antec-Fusion-HTPC:~$ sudo /etc/cron.daily/mythtv-backend 
2006-12-18 20:22:06.136 DataDirect, Error: Creating temp file from template '/tmp/mythtv_post_XXXXXX'
                        eno: Permission denied (13)
2006-12-18 20:22:06.138 DataDirect, Error: Creating temp file from template '/tmp/mythtv_result_XXXXXX'
                        eno: Permission denied (13)
2006-12-18 20:22:06.138 DataDirect, Error: Creating temp file from template '/tmp/mythtv_cookies_XXXXXX'
                        eno: Permission denied (13)
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
oneiros@Antec-Fusion-HTPC:~$ ps -A|grepmysql
bash: grepmysql: command not found
oneiros@Antec-Fusion-HTPC:~$ ps -A|grep mysql
 4683 ?        00:00:00 mysqld_safe
 4741 ?        00:00:05 mysqld
oneiros@Antec-Fusion-HTPC:~$ 

I'm also seeing some strange errors running mythfilldatabase, it's not ALL errors,  it succeds on some, and maybe this is because of how many non-channels show up as channels in the QAM scan (?) but here's a paste of those errors, I'll report back whether program guide is actually showing up in mythfrontend when filldatabase is done....  Here's errors from mythfilldatabase paste (similar ones recur very very quickly when errroring):

2006-12-18 20:25:51.043 DB Error (Inserting into dd_productioncrew):
Query was:
INSERT INTO dd_productioncrew        ( programid,  role,  givenname,  surname,  fullname) VALUES ('MV0479100000', 'Executive_Producer', 'Jennifer', 'Ogden', 'Jennifer Ogden')
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_productioncrew' doesn't exist

Add here's a successful section I grabbed quick...  I'm fairly puzzled, but hopefully making progress...:

06-12-18 20:36:01.946 
2006-12-18 20:36:01.946 Checking day @ offset 5, date: Sat Dec 23 2006
2006-12-18 20:36:01.947 Data refresh needed because no data exists for day @ offset 5 from 6PM - midnight.
2006-12-18 20:36:01.947 Refreshing data for Sat Dec 23 2006
2006-12-18 20:36:01.948 Retrieving datadirect data.
2006-12-18 20:36:01.948 Grabbing data for Mon Dec 18 2006 offset 5
2006-12-18 20:36:01.948 From Sat Dec 23 05:00:00 2006 to Sun Dec 24 05:00:00 2006 (UTC)
2006-12-18 20:36:01.948 Grabbing listing data
--20:36:01--  [http://datadirect.webservices.zap2it.com/tvlistings/xtvdService](http://datadirect.webservices.zap2it.com/tvlistings/xtvdService)
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

---

### Post by oneiromancer on 2006-12-18
Well, mythfilldatabase finished, but still no guide data showing up in program guide.... neither for OTA-ATSC nor for QAM (though QAM didnt get channel names so I can see that being harder to match up guide data for.... )  I'm at a loss...  here is how mythfilldatabase ended (EDIT /PS - myth is also running a lot slower now, ie menu transitions are suddenly very sluggish, in some case VERY sluggish, like 30-45 seconds for a transition from button press...  does that give any clues or whatnot?  Should be plenty of CPU, running on an Athlon 64 X2 4200...  also, whenj I start up myth frontend, I get a screen saying /var/lib/pictures could not be opened or does not exist or something...  no idea why, I haven't touched it and never used it or referenced it to my knowledge....  just one more bit of weirdness I guess, unless it has significance to you...):
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

2006-12-18 20:40:53.637 Failed testing program view table.
2006-12-18 20:40:53.648 New DB connection, total: 4
2006-12-18 20:40:53.649 Connected to database 'mythconverg' at host: localhost
2006-12-18 20:40:53.650 New DB connection, total: 5
2006-12-18 20:40:53.650 Connected to database 'mythconverg' at host: localhost
2006-12-18 20:40:53.651 Failed to fetch some program info
2006-12-18 20:40:53.651 Adjusting program database end times.
2006-12-18 20:40:53.651     0 replacements made
2006-12-18 20:40:53.651 Marking generic episodes.
2006-12-18 20:40:53.652     Found 0
2006-12-18 20:40:53.652 Marking repeats.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Unmarking new episode rebroadcast repeats.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Marking episode first showings.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Marking episode last showings.
2006-12-18 20:40:53.654     Found 0
2006-12-18 20:40:53.654 Grabbing next suggested grabbing time
2006-12-18 20:40:54.220 DataDirect: BlockedTime is: 2006-12-18T20:40:49
2006-12-18 20:40:54.221 DataDirect: NextSuggestedTime is: 2006-12-19T06:30:44
2006-12-18 20:40:54.223 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2006-12-18 20:40:54.226 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-12-18 20:40:54.227 Using protocol version 31
2006-12-18 20:40:54.227 MainServer::HandleAnnounce Monitor
2006-12-18 20:40:54.228 adding: Antec-Fusion-HTPC as a client (events: 0)
2006-12-18 20:40:54.228 MainServer::HandleAnnounce Monitor
2006-12-18 20:40:54.228 adding: Antec-Fusion-HTPC as a client (events: 1)
2006-12-18 20:40:54.230 mythfilldatabase run complete.
2006-12-18 20:40:54.231 Reschedule requested for id -1.
2006-12-18 20:40:54.234 MythSocket(818b3b8:-1): writeStringList: Error, socket went unconnected.
2006-12-18 20:40:54.246 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
oneiros@Antec-Fusion-HTPC:~$ ps -A|grep myth
 7612 pts/0    00:00:01 mythbackend
oneiros@Antec-Fusion-HTPC:~$ 2006-12-18 20:42:07.773 MainServer::HandleAnnounce Monitor
2006-12-18 20:42:07.773 adding: Antec-Fusion-HTPC as a client (events: 0)
2006-12-18 20:42:07.774 MainServer::HandleAnnounce Monitor
2006-12-18 20:42:07.774 adding: Antec-Fusion-HTPC as a client (events: 1)
2006-12-18 20:42:07.897 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2, exiting

---

### Post by superm1 on 2006-12-20
> **oneiromancer said:**
> Well, mythfilldatabase finished, but still no guide data showing up in program guide.... neither for OTA-ATSC nor for QAM (though QAM didnt get channel names so I can see that being harder to match up guide data for.... )  I'm at a loss...  here is how mythfilldatabase ended (EDIT /PS - myth is also running a lot slower now, ie menu transitions are suddenly very sluggish, in some case VERY sluggish, like 30-45 seconds for a transition from button press...  does that give any clues or whatnot?  Should be plenty of CPU, running on an Athlon 64 X2 4200...  also, whenj I start up myth frontend, I get a screen saying /var/lib/pictures could not be opened or does not exist or something...  no idea why, I haven't touched it and never used it or referenced it to my knowledge....  just one more bit of weirdness I guess, unless it has significance to you...):
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

2006-12-18 20:40:53.637 Failed testing program view table.
2006-12-18 20:40:53.648 New DB connection, total: 4
2006-12-18 20:40:53.649 Connected to database 'mythconverg' at host: localhost
2006-12-18 20:40:53.650 New DB connection, total: 5
2006-12-18 20:40:53.650 Connected to database 'mythconverg' at host: localhost
2006-12-18 20:40:53.651 Failed to fetch some program info
2006-12-18 20:40:53.651 Adjusting program database end times.
2006-12-18 20:40:53.651     0 replacements made
2006-12-18 20:40:53.651 Marking generic episodes.
2006-12-18 20:40:53.652     Found 0
2006-12-18 20:40:53.652 Marking repeats.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Unmarking new episode rebroadcast repeats.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Marking episode first showings.
2006-12-18 20:40:53.653     Found 0
2006-12-18 20:40:53.653 Marking episode last showings.
2006-12-18 20:40:53.654     Found 0
2006-12-18 20:40:53.654 Grabbing next suggested grabbing time
2006-12-18 20:40:54.220 DataDirect: BlockedTime is: 2006-12-18T20:40:49
2006-12-18 20:40:54.221 DataDirect: NextSuggestedTime is: 2006-12-19T06:30:44
2006-12-18 20:40:54.223 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2006-12-18 20:40:54.226 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-12-18 20:40:54.227 Using protocol version 31
2006-12-18 20:40:54.227 MainServer::HandleAnnounce Monitor
2006-12-18 20:40:54.228 adding: Antec-Fusion-HTPC as a client (events: 0)
2006-12-18 20:40:54.228 MainServer::HandleAnnounce Monitor
2006-12-18 20:40:54.228 adding: Antec-Fusion-HTPC as a client (events: 1)
2006-12-18 20:40:54.230 mythfilldatabase run complete.
2006-12-18 20:40:54.231 Reschedule requested for id -1.
2006-12-18 20:40:54.234 MythSocket(818b3b8:-1): writeStringList: Error, socket went unconnected.
2006-12-18 20:40:54.246 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
oneiros@Antec-Fusion-HTPC:~$ ps -A|grep myth
 7612 pts/0    00:00:01 mythbackend
oneiros@Antec-Fusion-HTPC:~$ 2006-12-18 20:42:07.773 MainServer::HandleAnnounce Monitor
2006-12-18 20:42:07.773 adding: Antec-Fusion-HTPC as a client (events: 0)
2006-12-18 20:42:07.774 MainServer::HandleAnnounce Monitor
2006-12-18 20:42:07.774 adding: Antec-Fusion-HTPC as a client (events: 1)
2006-12-18 20:42:07.897 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2, exiting
Are you using a non standard database name for some reason?  It appears as though these errors are trying to access a database that may be a little bit different here.  If you are using a nonstandard database, have you been consistent to list it **everywhere?**

---

### Post by oneiromancer on 2006-12-20
Nope, name as far as I know is mythconverg.  I had some difficulties with the database early on than wound up resulting in reinstalling myth, brief summary is I had no password on root account when I installed, I added a password later and, despite doing a pkg reconfigure where I gave it correct login info and password, it kept having problems logging in, and then continued to have problems after I changed password back to being empty (I may have had to resinstall mysql too, I forget, it wasn't easy taking away password to leave it empty).  Haven't had any issues with that since reinstall though.

I *did* however originally run mythtv-setup (or possibly re-run it) as the mythtv user, which is why I was trying to get help exporting display while "su - mythtv"ing to that account, I found instructions (which I've had troible relocating the one time I looked for again) in the dapper version of a myth-ubuntu setup guide, instructions that were left out of the edgy version, for enabling GDE (GDM?) login on the mythtv account...  the problems I have logging in to mythtv user from gnome login now appear to be different, before I think it said no such user or something, now it gives me an error box with either gibberish or impossibly small text (conceivable that on a different display I could read it, but I have native-ish resolution on my plasma and most text is very clear, so I haven't bothered trying).  

Is it time to just reinstall myth and/or mysql?  That would be my resort at this point on my own, but of course you're the expert, I defer to you, and if there's any more diagnostic info I can provide, please let me know...

---

### Post by superm1 on 2006-12-20
> **oneiromancer said:**
> Nope, name as far as I know is mythconverg.  I had some difficulties with the database early on than wound up resulting in reinstalling myth, brief summary is I had no password on root account when I installed, I added a password later and, despite doing a pkg reconfigure where I gave it correct login info and password, it kept having problems logging in, and then continued to have problems after I changed password back to being empty (I may have had to resinstall mysql too, I forget, it wasn't easy taking away password to leave it empty).  Haven't had any issues with that since reinstall though.

I *did* however originally run mythtv-setup (or possibly re-run it) as the mythtv user, which is why I was trying to get help exporting display while "su - mythtv"ing to that account, I found instructions (which I've had troible relocating the one time I looked for again) in the dapper version of a myth-ubuntu setup guide, instructions that were left out of the edgy version, for enabling GDE (GDM?) login on the mythtv account...  the problems I have logging in to mythtv user from gnome login now appear to be different, before I think it said no such user or something, now it gives me an error box with either gibberish or impossibly small text (conceivable that on a different display I could read it, but I have native-ish resolution on my plasma and most text is very clear, so I haven't bothered trying).  

Is it time to just reinstall myth and/or mysql?  That would be my resort at this point on my own, but of course you're the expert, I defer to you, and if there's any more diagnostic info I can provide, please let me know...
This probably dates back to reasoning why you had things messed up in the first place with guide data among a few other things.  
You've got two solutions at this point,
1) either find all places that mythconverg.dd_v_program is referenced and replace them with mythconverg.  
  A) /etc/mythtv/mysql.txt
  B) all users' ~/.mythtv/mysql.txt
  C) /usr/share/mythtv/mysql.txt if it isn't a symlink
  D) drop this table from mysql if it exists
  E) dpkg-reconfigure mythtv-common, and set the name here
  F) Any references to this other table in the normal mythconverg table
2) Clean setup of myth packages
   A) Remove all myth packages and their configurations.  (Be sure to purge configuration)
   B)Make sure that mysql has dropped all mythconverg and mythconverg.dd_v_program tables.  (This can be easily done through phpmyadmin if your not comfortable with mysql command line syntax)
   C) Remove any user's ~/.mythtv directories.  
   D) Remove /etc/mythtv if its not done for you.  
   E) Remove /usr/share/mythtv if its not done for you.  (These should all be cleaned up during package removal, but at this point you've got some wacky things going on anyhow)

I'm not sure how you managed to have such a convoluted setup here, perhaps some mysql database corruption had occurred at some point.  If thats the case, then you may just be better opting for the second option.   Note, you shouldn't have any needs to reinstall the mysql packaging,  just drop the databases.

---

### Post by oneiromancer on 2006-12-21
Hey SuperM, thanks for the suggestions, sorry it took me a day or two to try anything out....   I was curious to see if there *were* any references to "mythconverg.dd_v_program" like you predicted, but  in all the places you listed (/etc/mythtv/mysql.txt, all users' ~/.mythtv/mysql.txt, /usr/share/mythtv/mysql.txt ) it just said mythconverg.  Wouldn't dd_v_program be a table reference within the database, not a database name?  Could that be a valid table reference for myth?  I did do the dpkg-reconfigure mythtv-common FYI, and that showed mythconverg as well.    Knowing there were no references, does option 2 still make sense?  I'm not sure if I know how to "purge", in synaptic pkg mngr I can "remove completely"....  Would I be better off reinstalling from source or using synaptic again?  or apt-get?  What about the mythtv user, after I initially ran setup from my own account, I exited with incomplete setup and got a warning that there were no channels and asked to correct or if I "knew what I was doing", I chose the latter....  and then couldn't start up mythtv-setup again until I enabled Gnome login for mythtv user.....  I think that included doing a resintall of myth, but I forget just now...    and now I can't log in to mythtv user again, for whatever reason.... <sigh>  Appreciate your help...

---

### Post by superm1 on 2006-12-25
> **oneiromancer said:**
> Hey SuperM, thanks for the suggestions, sorry it took me a day or two to try anything out....   I was curious to see if there *were* any references to "mythconverg.dd_v_program" like you predicted, but  in all the places you listed (/etc/mythtv/mysql.txt, all users' ~/.mythtv/mysql.txt, /usr/share/mythtv/mysql.txt ) it just said mythconverg.  Wouldn't dd_v_program be a table reference within the database, not a database name?  Could that be a valid table reference for myth?  I did do the dpkg-reconfigure mythtv-common FYI, and that showed mythconverg as well.    Knowing there were no references, does option 2 still make sense?  I'm not sure if I know how to "purge", in synaptic pkg mngr I can "remove completely"....  Would I be better off reinstalling from source or using synaptic again?  or apt-get?  What about the mythtv user, after I initially ran setup from my own account, I exited with incomplete setup and got a warning that there were no channels and asked to correct or if I "knew what I was doing", I chose the latter....  and then couldn't start up mythtv-setup again until I enabled Gnome login for mythtv user.....  I think that included doing a resintall of myth, but I forget just now...    and now I can't log in to mythtv user again, for whatever reason.... <sigh>  Appreciate your help...

Sorry for the long delay in response, aside from it being the holidays, I am moving this week :)


That's surprising that the odd database name never popped up in any of those locations.  I've never seen anything in my logs refer to databases like that though (or tables from a database for that matter).  Purging is the same thing as removing completely in synaptic.  The command line compliment uses that terminology, so i'm used to that.  I'm not sure where at this point the database could have been coming from.   I still think it is a good idea to do though because it gives you a very clean slate, especially if you have nothing to lose in the process.  

As for getting the gnome login for mythtv user, you would have to set the password for the user after its generated, and should then be able to login at the login screen as you desire.

---

