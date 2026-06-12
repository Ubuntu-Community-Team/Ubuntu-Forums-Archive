---
title: "boinc authorization failure"
date: 2006-09-12
forum: Desktop Environments
---

### Post by psyncho on 2006-09-12
Hi, I just wanted to post some stuff I had previously had problems with for anyone else encountering these issues when trying to use boinc.

For a while I was getting authorization errors with boinc.  I was doing a couple things wrong.  One was, when you run boinc, its installed as a daemon, so you have to run the boinc_cmd command instead. E.g., to attach to a project you would do 
boinc_cmd --project_attach url key

The other thing that went wrong, was somehwere along the way, some configuration and installation files for boinc were put into my user directory.  Well, this will mess boinc up if its running as a daemon outside of the user directory (which is the default if you install from aptitude or some package maintainer software).  

Thus, get rid of anything boinc related in your user directory (if you're paranoid you can copy it into a directory such as olc_boinc and delete when you're comfortable).

Here's a link to another forum where some people had this problem:

[http://boinc.berkeley.edu/dev/forum_thread.php?id=685](http://boinc.berkeley.edu/dev/forum_thread.php?id=685)

---

### Post by emarkay on 2006-10-08
I (and another user there) am having a problem getting BOINC running here in Ubuntu.  I am using the client that is avaialbe in Ubuntu, and while I am sure it's a BOINC and configuration problem, I wanted to let others HERE know what I [hopefully will] find out THERE.  Anyone HERE who may know anything more, feel free to add your info here.  THANKS!

[http://setiathome.berkeley.edu/forum_thread.php?id=34263](http://setiathome.berkeley.edu/forum_thread.php?id=34263)

---

### Post by citybird on 2008-01-09
ok guys i am haveing similar problem.

What I would like to know is how can i get the command line boinc-client to work without the gui boinc-manager.

what is the command to attach to a project without creating files in your home dir?

wait i found the problem...

with boinc_client the command is --attach_project (this is the one you should not use)
with boinc_cmd the command is --project_attach (this is the one you should use)

what monkey thought this was a good idea??
find some consistency people!!

---

### Post by citybird on 2008-01-09
now after i attach i get the following:
> $ boinc_cmd --get_state
======== Projects ========
1) -----------
   name: SETI@home
   master URL: [http://setiathome.berkeley.edu/](http://setiathome.berkeley.edu/)
   user_name:
   team_name:
   resource share: 100.000000
   user_total_credit: 0.000000
   user_expavg_credit: 0.000000
   host_total_credit: 0.000000
   host_expavg_credit: 0.000000
   nrpc_failures: 1
   master_fetch_failures: 0
   master fetch pending: no
   scheduler RPC pending: no
   attached via Account Manager: no
   ended: no
   suspended via GUI: no
   don't request more work: no
   disk usage: 0.000000
   last RPC: 1199899673.734768
   project files downloaded: 0.000000


Where is my username and team name?? 
why do none of my settings show?

---

