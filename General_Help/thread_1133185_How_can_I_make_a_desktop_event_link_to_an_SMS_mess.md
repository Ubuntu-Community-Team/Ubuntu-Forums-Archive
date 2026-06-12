---
title: "How can I make a desktop event link to an SMS message?"
date: 2009-04-22
forum: General Help
---

### Post by tarahmarie on 2009-04-22
Hi, all:

I have notifications popup from time to time on my desktop.  They might be cron jobs, pidgin notifications, new emails from certain people, completed processes, whatever.  

I'd like to know if there's any protocol by which I can link events like a Pidgin notification or cron job to an SMS message sent to my phone?

Thanks!

---

### Post by aeiah on 2009-04-22
you'd probably have to code it yourself. you could catch these notifications from dmesg and dbus and write a fancypants script that sends a message via an online sms service...

there are programs for high availability clusters and virtual machines and such that'll monitor various things for you. heartbeat is great, and can probably be adapted because its really flexible. i think it already has a feature for reporting crashes and service errors to an email address. i guess there's a service somewhere on the net that'll convert incoming email to sms

im just thinking out loud though really. i dont think a simple solution exists but it isnt impossible.

---

### Post by tarahmarie on 2009-04-22
Well, I like challenges.  It should be relatively simple to get from email to SMS based on the services I've seen, so the real question is how to identify the desktop events I WANT notifications on, and translate that to an email. 

I've read the man page on dmesg, and it seems like a kernel notification command.  

Theoretically, there should be a log of a given event, like a popped up notification...where do I find that?

---

