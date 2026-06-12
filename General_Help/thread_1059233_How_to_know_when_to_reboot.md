---
title: "How to know when to reboot?"
date: 2009-02-03
forum: General Help
---

### Post by Krupski on 2009-02-03
Hi all,

When running the GUI version of Ubuntu, *some* updates end with "the computer must be rebooted - reboot now?" (something like that).

However, in Server, I use "apt-get -V update" and then "apt-get -V dist-upgrade" to install updates.

However, they *never* say if a reboot is necessary. So, as a precaution (until I know better), I do the following:

(1) Update
(2) Sync
(3) Pause 10 seconds
(4) Reboot

Of course, all the rebooting eventually catches up with the FSCK count on the hard drives and then the restart takes 20 minutes or so (a real pain).

I also simply don't like the idea of constantly rebooting a perfectly stable OS.

So... my question is... how do I know when I *HAVE* to reboot after an update (in Server)?

Thanks in advance!

-- Roger

---

### Post by jerome1232 on 2009-02-03
The only time I ever reboot my server is if a kernel upgrade comes through, other than that it's just whatever service that got upgraded needs to be restarted.

---

### Post by todak on 2009-02-03
The only time I ever reboot is when a newer kernel or video driver is installed. Else I log out and log in after updates.

---

### Post by gjoellee on 2009-02-03
You really don't HAVE to reboot any time, but it is required if you want a new kernel/driver to take effect. I would also reboot once a week, becuase even Linux gets slightly slower after a long time running!

---

### Post by whitegourd on 2009-02-03
For my servers I would only reboot whenever there is a kernel upgrade.  When there are application updates, the server would restart the services automatically.

---

### Post by HermanAB on 2009-02-03
You sure don't need to reboot very often:
[herman@gw1 ~]$ uptime
 14:01:59 up 393 days, 11:38

Cheers,

Herman

---

### Post by Krupski on 2009-02-03
> **jerome1232 said:**
> The only time I ever reboot my server is if a kernel upgrade comes through, other than that it's just whatever service that got upgraded needs to be restarted.

Is that just the way "you do it", or is that *THE* way?

---

### Post by Krupski on 2009-02-03
> **todak said:**
> The only time I ever reboot is when a newer kernel or video driver is installed. Else I log out and log in after updates.

Well, I'm running a headless server, so there are no video updates (unless it installs the drivers for the motherboard's built in video - which I don't use anyway).

---

### Post by Krupski on 2009-02-03
> **whitegourd said:**
> For my servers I would only reboot whenever there is a kernel upgrade.  When there are application updates, the server would restart the services automatically.

I've seen services stopped, then updates applied, the services restarted. But, if this were all that was required, then why would GUI installations sometimes need a reboot?

It makes perfect sense to stop a service, update it, then restart it... but this also obviates the need for a full reboot... which makes me wonder why it's asked for at all... I'm confused.

---

### Post by Krupski on 2009-02-03
> **HermanAB said:**
> You sure don't need to reboot very often:
[herman@gw1 ~]$ uptime
 14:01:59 up 393 days, 11:38

Cheers,

Herman

My server has never crashed or "messed up" on it's own. I'm sure my uptime could be from the day it started until now. I just wonder why some updates ask for a reboot. 

In Gnome, the little "two arrows chasing each other" icon comes up when a reboot is need. How does the OS know when to ask for a reboot, and how can I find out when I'm NOT using the GUI (i.e running the server remotely via SSH)?

---

### Post by jerome1232 on 2009-02-03
> **Krupski said:**
> I've seen services stopped, then updates applied, the services restarted. But, if this were all that was required, then why would GUI installations sometimes need a reboot?

It makes perfect sense to stop a service, update it, then restart it... but this also obviates the need for a full reboot... which makes me wonder why it's asked for at all... I'm confused.

Since the kernel is the core of the os the only way to restart it is with a reboot.

---

### Post by cubeist on 2009-02-03
> **gjoellee said:**
> You really don't HAVE to reboot any time, but it is required if you want a new kernel/driver to take effect. I would also reboot once a week, becuase even Linux gets slightly slower after a long time running!

The slowdown you notice might be from particular programs accessing files that are written to the /tmp directory.  You could create a cron job to clean out the /tmp without a restart.

---

### Post by jeffathehutt on 2009-02-03
Generally, the only time you have to reboot is when there is a kernel update.

I have a feeling the GUI tells you to reboot just to make it easier for inexperienced users.  You could reload each updated module/driver into the kernel and not have to reboot.  Or, you can reboot and it will be done automatically.:D

---

### Post by Slim Odds on 2009-02-03
> **cubeist said:**
> The slowdown you notice might be from particular programs accessing files that are written to the /tmp directory.  You could create a cron job to clean out the /tmp without a restart.

Yes, if your server gets slower over time, you've got to look into what's causing that. A linux server should run for **long** periods of time without issue.

One of my biggest aggravations is when people keep giving advise that includes rebooting. The **ONLY** reason to reboot linux is a kernel update (and maybe a few drivers). Most drivers are loadable modules, that those just need to be reloaded.

One of the worst is when someone says: change your network config and then reboot!

That's non-sense.

---

### Post by whitegourd on 2009-02-03
> **Krupski said:**
> I've seen services stopped, then updates applied, the services restarted. But, if this were all that was required, then why would GUI installations sometimes need a reboot?

It makes perfect sense to stop a service, update it, then restart it... but this also obviates the need for a full reboot... which makes me wonder why it's asked for at all... I'm confused.

GUI installs? ... Probably easier for the user.  But for a headless server, I think the kernel updates would be the only time you need to really reboot.

There is something out there called "ksplice" that supposedly prevents the need of a reboot after a kernel update (not familar with it though, just heard about it).

---

### Post by jimv on 2009-02-03
> **Krupski said:**
> My server has never crashed or "messed up" on it's own. I'm sure my uptime could be from the day it started until now. I just wonder why some updates ask for a reboot. 

In Gnome, the little "two arrows chasing each other" icon comes up when a reboot is need. How does the OS know when to ask for a reboot, and how can I find out when I'm NOT using the GUI (i.e running the server remotely via SSH)?

The only updates that ask for reboots are kernel upgrades.  The Gnome updater app watches for those upgrades and if there hasn't been a reboot since the newer kernel was installed, it gives you the icon.

I don't think there is a way in the console to be notified of a "needed" reboot.  As far as I know, however, the automatic updater doesn't install kernel upgrades on it's own.  Someone could correct me on that though.

---

### Post by dcstar on 2009-02-03
> **Slim Odds said:**
> 
........
One of my biggest aggravations is when people keep giving advise that includes rebooting. The **ONLY** reason to reboot linux is a kernel update (and maybe a few drivers). Most drivers are loadable modules, that those just need to be reloaded.
........

Agreed - for a satisfactorily running system - but AFAIK some security updates also tie into a synchronised kernel update, so the only way to make the changes effective is to boot into the new kernel (even if you don't "think" you need the new kernel).

A lot of X updates may require a total reload of the graphical sub-system, so for most users prompting for a reboot is a simple way of achieving this.

---

