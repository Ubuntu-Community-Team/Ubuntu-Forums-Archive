---
title: "How do I run Evolution-2.2 from Cron?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by JoshWilson on 2005-08-12
Hello all! N00b Wilson here...

I've setup a desktop with Ubuntu 5.0.4 and am running Evolution to connect to my Microsoft Exchange environment here at our office. The system that I've installed Ubuntu on is our Mail distribution server that parses through alert e-mails etc...and diverts them to the appropriate personnel.

PROBLEM
My problem is that when I execute /usr/bin/evolution-2.2 from a cron instance the application never comes up. If I execute that same command from my login shell it runs just fine.

I'm assuming that I need to remedy this I need to use the --display or --screen flags for evolution to get the program running correctly but I'm not sure how those flags work.

Can someone please tell me how to get /usr/bin/evolution-2.2 to execute successfully from a cronjob and run on the console's GUI in Ubuntu?

Any help is appreciated!

---

### Post by PeP on 2005-08-12
I don 't understand why you want to do that: a gui without someone in front of it ... can it do something you can't do diirectly without gui???

---

### Post by JoshWilson on 2005-08-12
This system processes e-mails for our Administrative Inbox.  We receive hundreds of messages a day that have to be parsed and then redistributed to the appopriate administrative personnel.  Because of this, I have to ensure that Evolution is running so that the filters will continue to process.

I've written a perl script to check and see if Evolution is running.  If it isn't, it is supposed to launch it.  At that point, it immediately kicks off the process and then dies. I never even see a window or error pop-up.  I only know that it starts because I was monitoring the processes as the cron job ran.

I made a little bit of headway by changing the line "DisallowTCP=True" to "DisallowTCP=False" in the /etc/gdm/gdm.conf file.  I was then able to execute the command directly from cron (rather than calling my perl script from cron) using the following line of text:

# CRON CONTENT
* * * * * /usr/bin/evolution-2.2 --display=10.15.3.59:0 & 2>/dev/null


When I try to set it up to run my perl script it always fails.   ](*,)  I'm using the following information to run my perl script but it doesn't run.

Any Ideas?

#CRON CONTENT - when trying perl script
* * * * * /usr/local/bin/evolution-check.pl

# EVOLUTION-CHECK.PL CONTENT
#!/usr/bin/perl
system("clear");
open(SCAN, "ps -ef |grep evolution-2.2 |head -1 |gawk '{print \$8}' |");
$RESULT=<SCAN>;
chomp($RESULT);
close(SCAN);

if ($RESULT eq "evolution-2.2")
        {
        print("It's runnin' already runnin' you big dummy!!!\n");
        goto EOF;
        }
else
        {
        print("Starting the Evolution application now...\n");
        system("/usr/bin/evolution-2.2 --display:10.15.3.59:0 \&");
        }

EOF:

---

