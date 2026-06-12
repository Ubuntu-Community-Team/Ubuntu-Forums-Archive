---
title: "problem with executing crontabs - syncevolution"
date: 2009-01-10
forum: General Help
---

### Post by NathanScrivener on 2009-01-10
I have set up syncevolution to sync with Scheduleworld. I have placed the following into crontab:

*/10 * * * * syncevolution scheduleworld > /home/nathan/schedule.log

The problem is, the command 'syncevolution scheduleworld' runs fine when I type it in from the terminal, but when executed automatically the crontab log shows the following:

11:40:05 [ERROR] todo: not found: ''

The syncevolution log says:

"GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks
due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Not running within active session)"

I'm fairly new to linux and am finding this a bit over my head, but really want my data synced with my phone :-(

My system is Linux Mint 6.0, based on Ubuntu 8.10

Please can somebody help?

p.s. I restarted cron after making my changes using 'sudo /etc/init.d/cron restart' and that didn't help

---

### Post by dcstar on 2009-01-10
> **NathanScrivener said:**
> I have set up syncevolution to sync with Scheduleworld. I have placed the following into crontab:

*/10 * * * * syncevolution scheduleworld > /home/nathan/schedule.log

The problem is, the command 'syncevolution scheduleworld' runs fine when I type it in from the terminal, but when executed automatically the crontab log shows the following:

11:40:05 [ERROR] todo: not found: ''

The syncevolution log says:

"GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks
due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Not running within active session)"

I'm fairly new to linux and am finding this a bit over my head, but really want my data synced with my phone :-(

My system is Linux Mint 6.0, based on Ubuntu 8.10

Please can somebody help?

p.s. I restarted cron after making my changes using 'sudo /etc/init.d/cron restart' and that didn't help

Is this a GUI program?, if so then do a search on how you have to set up these things in cron jobs.

The cron environment is different from a user shell, so do not make the assumption that because it works in user land it will also work in cron.

---

### Post by NathanScrivener on 2009-01-10
Thank you for your reply. The program I am trying to execute is for the command line, it does not have a GUI.

I am trying to follow your advice so looked up 'crontab environment', which from google I understand defaults to:

HOME=user's-home-directory
LOGNAME=user's-login-id
PATH=/usr/bin:/usr/sbin:.
SHELL=/usr/bin/sh

I came across this comment a couple of times:

"Users who desire to have their .profile executed must explicitly do so in the crontab entry or in a script called by the entry." (although none of the pages I visited gave the command to do so)

I found my .profile in /home, and it is as follows:

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


I am still confused :confused:

If you could offer any further advice I would be most grateful.

---

### Post by NathanScrivener on 2009-01-10
Further to my last post I created the following script to execute the command:

#/bin/bash

./home/nathan/.profile
/usr/bin/syncevolution scheduleworld


It still isn't working though :(

---

### Post by NathanScrivener on 2009-01-11
... still no luck ... i would be MOST grateful if anyone can offer some advice! :confused:

---

### Post by NathanScrivener on 2009-01-12
[[ bump ]]

---

### Post by hermogene on 2009-01-17
I found out a dirty issue:

rxvt -e /usr/bin/syncevolution *profile*

Rxvt is a terminal, which allows executing some command, as gnome-terminal (with -e or -x)... The annoying part is that it pops up when you won't expect it (at least if you don't know exactly what time it is...), I think the terminal could be run minimized.

Tell me if it works!

---

### Post by NathanScrivener on 2009-01-17
solved my problem by using the GUI front end Genisys.

thanks

---

### Post by hermogene on 2009-01-17
Mmmhhh... for the sake of elegance:
Eterm -i -e syncevolution *profile*
... is working!

---

