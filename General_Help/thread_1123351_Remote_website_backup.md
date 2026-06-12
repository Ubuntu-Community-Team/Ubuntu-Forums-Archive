---
title: "Remote website backup"
date: 2009-04-12
forum: General Help
---

### Post by TWD-Tony on 2009-04-12
Sorry if this is posted in the wrong forum, please move it if it is...

I am a Linux Noob (yeah you have heard it all before I know)

I recently wiped my windozeXP machine and installed Ubuntu - which i think is great (a learning curve but fun)

What I am trying to do is setup a remote backup system for several website's that I run, some of them are hosted on Mosso with no shell / SSH access so what I really need is something that will grab not only the web files but will also grab SQL DB backups from the servers.

I think I know how to grab the files via cron (although if someone wants to post a how to I would be very greatful) but the SQL has me stumped, I can't decide if I need to run a cron on the server to backup the SQL to a file or I can remote login to the SQL and execute a backup / copy to my PC?

Thanks

---

### Post by aaronp on 2009-04-14
not sure about getting the SQL data. Suggest python would have some mysql libraries that you could use to query the databases and write the same data to your own local or online backup mysql databases (or some other file types if desired). 
You could write the python program to do what you need to do and then run it on a cron schedule.

In regards to web data I have a shell script in which I use wget to login to the ftp server on the hosting site.
I set the shell script to run each night on a cron job.
This is a good reliable solution for me that I just set up months ago and it never fails (Unless my son manages to turn of the PC without me knowing!!)
I am going to look into replacing this with lftp or rsync though, as I would prefer to do it incrementally as opposed to downloading the full site each night even though nothing or little has changed.

hth
Aaron

---

