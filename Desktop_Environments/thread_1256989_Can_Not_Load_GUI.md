---
title: "Can Not Load GUI"
date: 2009-09-03
forum: Desktop Environments
---

### Post by sirius1 on 2009-09-03
Ubuntu 8.04.1

Currently I can only use the cli, can't load gui, so operating off of memory here as best I can.

My desktop theme is Slickness Black .09.

While replacing default icons, with some I found at "kde-look.orgin" I was giving myself root privilege for directores I could not access, i.e., usr, evolution, any application icon I wanted to change and couldn't. Some of those apps were Evolution, trash, home...

Things were going fine, until I ended up with about 20 small trash icons on my bottom panel.

Then, things went downhill in a hurry. I could not move windows around the desktop, or right-click on the desktop.

I had my network connections established, but could not print, the terminal was flakey.

When I tried to power off I clicked the little green man and was left with nothing but my slickness black desktop, no panels, no way to power down.

I got out of it, via the Alt SysRq sequence.

When I powered back up I got the following message, spamAssassin Mail filter Daemon disabled, sce /etc/default/spamassassin sed: couldn't write 85 items out to stoudt: No space left on device.

Please edit the file /etc/MailScanner! Mailscanner.conf according to your needs. Then configure Sendmail ore ex.m for use with mailscannser.

After you are done you will have to edit /etc/default/mailscanner as well. Set variable run_mailscanner to /, and then type "etc/init.d/mailscanner start" to start up the daemon.

sed: couldn't flush stdout: No space left on device.
sed: couldn't flush stdout: No space left on device.

This is probably the start of a long process. *Before* this error messsage, I went back in, and set the directories i.e. usr, evolution ... back to root instead of my admin username.

I really appreciate/value anyone's time on my problem.

Larry

---

### Post by jerrrys on 2009-09-03
hi larry

for what its worth, i do know from past experience that playing with evolution can take out your desktop.  don't know what it will do to your custom theme, but you may want to try reloading it...

---

### Post by hal10000 on 2009-09-03
> sed: couldn't flush stdout: No space left on device
your / partition is 100% full.
I don't know if this happened because you changed the permissions, but **!!!!!NEVER!!!!** change permissions on directories or files you didn' create yourself. Maybe you messed up your whle system.
I guess the best thing to do is to somehow make place on your partition by deleting files you don't need

---

### Post by sirius1 on 2009-09-03
Currently, I can only use the CLI and don't know how to reload my desktop or custom theme.

If Evolution did take out my desktop, can you point me to instructions to restore an earlier desktop, I have backups, from the command line.

Thanks, jerrys.

---

### Post by jerrrys on 2009-09-03
[https://answers.launchpad.net/ubuntu/+source/evolution/+question/57329](https://answers.launchpad.net/ubuntu/+source/evolution/+question/57329)

also may want to try **fix broken packages**.  its a option in grub during the boot process, may get lucky...

---

### Post by sirius1 on 2009-09-03
Thanks Hal10000, seriously, lesson learned...

I noticed my root is 100% full, like you say.

Yes, I know it happened when I was changing directoies I didn't create myself.

I can do what you say, but was wondering if it could be restored from backup easier.

Thanks again.

---

### Post by regala on 2009-09-03
> **sirius1 said:**
> Thanks Hal10000, seriously, lesson learned...

I noticed my root is 100% full, like you say.

Yes, I know it happened when I was changing directoies I didn't create myself.

I can do what you say, but was wondering if it could be restored from backup easier.

Thanks again.

if you have one backup, yes. If not, try apt-get clean.

---

### Post by sirius1 on 2009-09-03
Thanks regala...I'm on it...got to leave for most of the day.

Again, thanks to all.

Larry

---

### Post by sirius1 on 2009-09-03
Thanks jerrys, will do, any luck is good luck...

Montana, a good state, my cousin's retiring there in March.

Mr. Minnesota ...here.

---

### Post by sirius1 on 2009-09-26
> **regala said:**
> if you have one backup, yes. If not, try apt-get clean.

Finding a clean backup took a few weeks, as I went along changing things it corrupted my backups.

I finally found a good backup and ran a Simple Backup Restore which resolved a number of issues.

---

