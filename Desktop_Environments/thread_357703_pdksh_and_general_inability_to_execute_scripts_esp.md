---
title: "pdksh and general inability to execute scripts especially at boot"
date: 2007-02-10
forum: Desktop Environments
---

### Post by tashazo on 2007-02-10
Hi, I'm on Dapper with Gnome.  I have several apps starting with Sessions.  I started having problems executing startup commands a little while ago, while installing [Remind.]("http://www.linux.com/article.pl?sid=06/07/24/1516241")  I'm not sure if it's correct, but the "/usr/bin/remind -z -kgxmessage -title reminder %s & ~/.reminders & " I have doesn't start it at all.   I tried that command in Terminal, but it didn't work either, saying: [1] 25473
[2] 25474
Remind: '-i' option: Missing '=' sign  
blablabla, and:  bash: /home/natasha/.reminders: Permission denied
The thing is, no matter how I change .reminders permissions, I get either Permission denied or cannot find .reminders or something.  .reminders isn't a script, it's just a text file with my reminders, really, so I don't know how it should be here.  I couldn't get crontab to work with remind either...

So I assume it has something to do with that.  Then, I'm trying to get [Conky]("http://conky.sourceforge.net/") to startup with Gnome, with startup scripts (which DO work in Terminal, no problem) with different "sleep" parameters like 60 or 10 sec, but none work.  Conky will not startup automatically, so I have put a panel-app-launcher for it instead.  (that works)

Any help'd really be appreciated...Thanks!

---

