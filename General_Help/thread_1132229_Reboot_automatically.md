---
title: "Reboot automatically"
date: 2009-04-21
forum: General Help
---

### Post by Libertario on 2009-04-21
Hi all,

I would like system reboot automatically every morning but I don't know how to do without root privileges.

I can use "/sbin/reboot" but to do it I need root privileges.

I'm working with Ubuntu Intrepid.

Any suggestions?


Thanks,
Libertario.

---

### Post by Alterax on 2009-04-21
> **Libertario said:**
> Hi all,

I would like system reboot automatically every morning but I don't know how to do without root privileges.

I can use "/sbin/reboot" but to do it I need root privileges.

I'm working with Ubuntu Intrepid.

Any suggestions?


Thanks,
Libertario.

Well, I'm not sure why you would want to do this...Linux very seldom needs rebooting; I have some systems that have been going for years without issue.

But, nonetheless you asked how (not if,) so I'll show you how to make a cron job--the ideal way of automating processes.  

As root or using sudo, make a file called /etc/cron.d/reboot

Here's what to put in it:

```
01 06 * * *    /sbin/reboot

```

The numbers represent time: In this case, the reboot occurs every day of the week at 06:01 AM.

Once you have made the file, restart the cron service so that it will pick up the new entry with the following command:

sudo /etc/init.d/cron restart

---

### Post by Libertario on 2009-04-26
Hi Alterax,

Thank you.  This is what I was looking for it.

---

### Post by Alterax on 2009-04-27
No problem!

Cron's a little cryptic at first, but it's really handy once you get the hang of it.  Learn to make your own BASH scripts, and you can be a really lazy (or alternatively "efficient") administrator.

I use it for a lot of maintenance tasks--one entry triggers a script every night to back up my laptop's settings and documents to the server, another entry runs every hour or so and tidies up my home folder and desktop--shuffling videos, documents, pictures, music, and source code to their proper directories.

It's really nice.  If you'd like, I can post a couple of things on how to do it.

---

