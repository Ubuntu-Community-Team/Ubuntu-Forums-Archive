---
title: "hostname &amp; workgroup"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Branta on 2006-08-18
I am setting up Samba with this howto: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=Samba]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=Samba")

How to I **find out** what **workgroup** I used at installation (if any)?

Can I **change the hostname** from what I used at installation and is reported by network-admin?

If so, **how do I do it**?

I can enter anything in /etc/samba/smb.conf but I want it to be in line with the system.


--- Bob ---

---

### Post by jimbren on 2006-08-18
You don't enter a workgroup name when you're installing Ubuntu, so you don't need to worry about that.  You should have your Samba config match whatever workgroup you are actually using.

As for hostname, you can change that by modifying the /etc/hostname file.  

I think you have to reboot for it to take effect, but I'm not certain.

---

### Post by Branta on 2006-08-18
Thanks for the quick reply.  

I found I can change the hostname with sudo -s and then 'hostname BOB-DESKTOP'

I looked at /etc/hostname and the new name is indeed there.

Yes, I had to reboot for the change to appear.

Thanks, Bob

---

