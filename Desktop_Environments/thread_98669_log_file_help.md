---
title: "log file help"
date: 2005-12-03
forum: Desktop Environments
---

### Post by astoltz on 2005-12-03
Hello all. Occasionally, i get the urge to browse through my log files - mostly just to satisfy myself that nothing is "strange" security-wise.  Trouble is, I'm not really sure what I should be looking for.  I've got a ssh server running, so I check the auth.log for login attempts and I've got postfix running so I check the mail.log but I never really see anything that looks out of place.  So am I just being paranoid, or am I missing something?  What should I be looking for in the logs?  Thanks.

---

### Post by amohanty on 2005-12-03
Well another way to look at logins is the ```
lastlog
``` command.

Heres what I did:

1. Install tripwire and chkrootkit (I think they are both in Universe)
2. Take box off of network
3. Run chkrootkit to check for anything vaguely dangerous
4. Initialize tripwire
5. Setup cron tasks to run chkrootkit and tripwire nightly and mail you the results
6. If you are worried about viruses, add clamav to the list as well.

Thats pretty much all you would need to do, for the most part. Heres the thing about security, if a cracker is really determined and _sufficiently_ skilled, the best you can hope for is to be notified asap. Other than that, as long as you are on top of updates, did not setup your mail/web server as an open proxy, and run the two apps mentioned above, you should be fine for the most part.

HTH
AM

---

### Post by astoltz on 2005-12-03
Well that's the thing.  If a cracker were to attempt to break in, what would show up in the log files to show the event?  

I run chkrootkit every now and then but it not in a cron job.  That's probably a good idea.  And I'll take a look at tripwire. Thanks for the suggestions.

---

### Post by amohanty on 2005-12-03
Usually its a login that you dont expect, as in root logged in at 3:00 am, 
Or more than 3 login attempts on the same account.
Multiple login attempts too close together.
Multiple incoming emails (to exploit any MTA vulnerebilities) too close together (might not be feasible if you have a high volume mail server)
Wierdo URLS in your web server logs if you run a web server.

Also do these 4 other things ot your todo list:

1. disallow root login via xdmcp (GUI)
2. disallow root login via ssh (in the sshd conf files)
3. allow root login only in tty1 (I think you set this in /etc/inittab) - so that physical presence would be required for root login
4. Also run nmap occasionally on all ports:
```
sudo nmap -vV -sS -p 1,65535 <your ip address>
```
This will report all ports that are open on your box. So if you have an unexpected port, you probably have a trojan.
you can install nmap from the universe repos.

Now the thing is, usually these things are not likely to happen since most critical vulnerebilities are addressed extremely quickly in FOSS unlike commercial software. Be paranoid, but within reasonable limits would be my advise.

HTH
AM

---

### Post by escobar on 2005-12-04
[QUOTE=amohanty]Well another way to look at logins is the ```
lastlog
``` command.

Heres what I did:

1. Install tripwire and chkrootkit (I think they are both in Universe)
2. Take box off of network
3. Run chkrootkit to check for anything vaguely dangerous
4. Initialize tripwire
5. Setup cron tasks to run chkrootkit and tripwire nightly and mail you the results
6. If you are worried about viruses, add clamav to the list as well.

Thats pretty much all you would need to do, for the most part. Heres the thing about security, if a cracker is really determined and _sufficiently_ skilled, the best you can hope for is to be notified asap. Other than that, as long as you are on top of updates, did not setup your mail/web server as an open proxy, and run the two apps mentioned above, you should be fine for the most part.

HTH
AM[/QUOTE]


Can you post a link to a tutorial or anything that explains how to do this stuff?

---

