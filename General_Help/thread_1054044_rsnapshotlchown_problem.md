---
title: "rsnapshot/lchown problem"
date: 2009-01-29
forum: General Help
---

### Post by Ubunt2u on 2009-01-29
i'm using rsnaphot to backup several servers.  the initial backup works fine, but the subsequent backup jobs are failing to remove updated and/or deleted files and folders.
when running rsnapshot -t daily i am getting the following error "require Lchown
Lchown module not found"
i've attempted to install Lchown with no luck.  After doing some research seems it's not available for debian distros? I'm using Ubuntu 8.04 server.
I'm pretty sure that fixing the Lchown issue with fix the issue with removing old/deleted files.
i went here [http://www.linuxquestions.org/questions/linux-software-2/rsnapshot-require-lchown-516423/](http://www.linuxquestions.org/questions/linux-software-2/rsnapshot-require-lchown-516423/)
and tried this but it didn't work.
has anyone else encountered this problem? 
can anyone help?
Thanks in advance

---

### Post by pdc124 on 2009-02-08
you need the Lchown perl modules , which in turn needs to be compiled.
This week is my first experiment with ubuntu server . Missing a few essential tools IMHO.

i sorted mine by 

sudo apt-get install build-essential

after that remove your cpan config 
rm -rf /home/user/.cpan

then start the cpan shell and re-run the cpan config, so it can find stuff

then install Lchown ( case sensitive) 

cpan>install Lchown


then quit cpan 

and it should be OK

---

### Post by Ubunt2u on 2009-02-09
Thanks! I'll give that a try.

---

### Post by Ubunt2u on 2009-02-17
LOL I somehow managed to get rid of the Lchown error, but now when rsnapshot runs as cronjob it backs up one (out of 4) servers to be backed up then quits.  No errors in rnsapshot.log (verbosity & error report levels both set to 5)

If i run rsnapshot daily manually, it runs perfectly.

---

### Post by pdc124 on 2009-02-19
whats your rsnapshot config
print it without the comment lines
ie print any line starting with an upper or lower case letter or a space

do  grep ^[A-Za-z\ ] /etc/rsnapshot.conf

if youve got comment lines starting with a space do

grep ^[A-Za-z] /etc/rsnapshot.conf

---

### Post by Ubunt2u on 2009-02-19
to be honest, at this point, with the different issues that keep popping up, I'm seriously considering scrapping it & starting from scratch.  Does any know if there's a preferred distro for rsnapshot?
I'm currently using Ubuntu 8.04 Hardy Herron Server.

---

### Post by pdc124 on 2009-02-19
ive had it running on gentoo and it was fairly straightforward to set up. Migrating to ubuntu was a PITA because even the server version appears not to come with a toolchain and rsnaphso wont work properaly without Lchown.

ive got it working using different config files ( rsnaphot -c option) 

1. from a script that mounts my wifes' windows laptop then backups up her stuff every 4 hours 

2. from a client machine that mounts the backup folder on the server and then backs up my /home and some custom scripts in /usr/local

I run it manually every so often and add to the exclude list 
eg *iso 
/home/me/local/.Trash
mozilla cache etc etc 

post your config file.  ( as above)

---

### Post by Ubunt2u on 2009-02-19
I'm running it manually (since it quit during cron last night) right now.  When it's done, i'll post rsnapshot.conf

I did come across a thread somewhere about troubles with cron & rsnapshot.  having to do with there being no mta for cron to report errors to.  i think i'll try that as well, since it's the automated backups i'm having the most trouble with.  sorta makes sense to me, when running manually, if it encounters any issues, it pauses for a bit, then continues.  maybe cron comes across the same issues, wants to report but has no mechanism to do so?

Seems the main types of errors it's encountering is
CIFS VFS:  server not responding
CIFS VFS:  No response to cmd 46 mid 49609
CIFS VFS:  Send error in read = -11

---

### Post by Ubunt2u on 2009-02-24
Just a quick follow up.  I installed mailx and now rsnapshot run from cron is running correctly.  There are some warnings, but it's doing what it's supposed to now,adding new files, removing old ones, etc.

Seems it was just dying when it was having issues in cron & couldn't report it.

---

