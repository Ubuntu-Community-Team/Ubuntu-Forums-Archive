---
title: "spamd error"
date: 2006-12-07
forum: Desktop Environments
---

### Post by wilstar on 2006-12-07
hi,
i have installed spamassassin with apt-get install...

But it doesn't ever work properly!

This is my error (i also have it when i do sudo apt-get upgrade):

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up spampd (2.30-11) ...
An override for "/var/cache/spampd" already exists, aborting
Warning: statoverride couldn't be created for /var/cache/spampd
An override for "/etc/spampd.conf" already exists, aborting
Warning: statoverride couldn't be created for /etc/spampd.conf
 * ERROR: Insufficient privileges. Retry as root
invoke-rc.d: initscript spampd, action "start" failed.
dpkg: error processing spampd (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 spampd
E: Sub-process /usr/bin/dpkg returned an error code (1)

why?

---

### Post by dcstar on 2006-12-07
> **wilstar said:**
> hi,
i have installed spamassassin with apt-get install...

But it doesn't ever work properly!

This is my error (i also have it when i do sudo apt-get upgrade):

sudo apt-get -f install
.....
why?

Firstly, you must use sudo when doing package installs, secondly, why stuff around with command lines when a perfectly good GUI interface is available for these things? (Synaptic).

---

### Post by Hadron Quark on 2006-12-27
Firstly : he did use sudo.
Secondly :If you dont have anything to offer, why reply? The command line is a lot faster for some. Now, do you know the spamd problem or you just want to pontificate and fart around without actually helping anyone?

---

### Post by dcstar on 2006-12-27
> **Hadron Quark said:**
> Firstly : he did use sudo.
Secondly :If you dont have anything to offer, why reply? The command line is a lot faster for some. Now, do you know the spamd problem or you just want to pontificate and fart around without actually helping anyone?

Firstly, yes, I notice that he did - my mistake for reading the "Retry as root" message.

Secondly, using Synaptic can (sometimes) provide more information as to why problems like this occur, as well as allow easy viewing of any other packages that may be available for upgrading and could well be related to strange issues like this.

It seems to me quite a few people are far too ready to tell users to use the command line when most users would be far better off using the GUI tools. All this seems to do (in a lot of cases) is cause problems further down the track, especially if people don't fully understand what they are doing in the terminal.

As for "actually helping", I was waiting for the person to come back and give us some results of trying to do it via Synaptic, but as you see from the time gap either the problem went away or a solution was found without having to come back to these forums.

---

### Post by OldSeaDog on 2007-01-05
Guess what - I used symaptic with exactly the same result,k in the terminal window.  Symaptic is just a pretty face on apt, so I am not sure how much more information can be obtained from an app that is executing the same code.  At its heart it is still dpkg  that is kicking up the fuss.

Having said that, is there is fix around?

The OldSeaDog and Chief Geekasaur

---

### Post by sm0ke0ut on 2007-03-08
just do:

rm /etc/init.d/spampd

apt-get remove spampd

It worked for me :-)

---

### Post by OldSeaDog on 2007-03-13
Unfortunately, it was no help.  The problem continued until I started from scratch and redid by hand the entire spamassassin configuration by uninstalling it, including config files, then starting ith a new install and reconfig.  Work continues in refining it, But I am seriously considering moving to webmail and letting someone else do the heavy lifting.

In short, I am following the advice of two well-known East Indian philosophers, called Bin Dar and Dun Dat.  I also have the Tshirt and am seriosly considering burning it.

BTW, to all you O'Toole's, O'Neills (note the 2 'L's) and O'Simonovitch's out there, HAPPY ST. PADDY'S DAY (Mar. 17 is just around the corner).  I have to be true to my roots somehow :)

OldSeaDog, the Geekosaur in Chief

---

