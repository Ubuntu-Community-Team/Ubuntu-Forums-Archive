---
title: "Boot problems."
date: 2013-10-22
forum: Desktop Environments
---

### Post by jimford on 2013-10-22
After upgrading (yeah - right!) my perfectly working 12.10 Xubuntu system to 13.04, I'm having numerous problems, starting with booting:

On initial power on I get the Xubuntu splash screen with the rotating segment. The screen then goes black and boot activity ceases and the machine becomes unresponsive and needs to be powered off. On restarting I get the Grub boot screen. If I select just a normal ubuntu start, the machine then boots satisfactorily and shows a crash icon. If I try to report the crash, nothing appears to happen. This happens every time.

I'd be grateful for any ideas, please.

Jim

---

### Post by oldfred on 2013-10-22
I do not know Xubuntu, but assume it also has its log files in /var/log. I would look at dmesg and see if first boot shows some sort of errors or long time between entries. Do not post entire dmesg as it is long, but if you have entries with long time stamp differences post the entries before & after.
If one install it is normal not to see grub menu and then after error to see grub menu so you can boot in recovery mode and make repairs. 
Is there anything involved that needs to come up to speed as boot process like external drive or connection to  network. They keep speeding up boot process, but then other external devices may not be fully up to speed??

---

### Post by Dennis N on 2013-10-22
> **oldfred said:**
> I do not know Xubuntu, but assume it also has its log files in /etc/logs. I would look at dmesg and see if first boot shows some sort of errors or long time between entries. Do not post entire dmesg as it is long, but if you have entries with long time stamp differences post the entries before & after.


Probably meant to say **/var/log** instead of /etc/logs 
In /var/log you will find the file **dmesg**.

---

### Post by oldfred on 2013-10-22
Thanks Dennis M., teach me to look at my system first to confirm rather than attempting to use oldfred's memory. :)

Fixed in post above.

---

### Post by Dennis N on 2013-10-22
@oldfred

Just a tiny lapse. Your work here is impressive, and I have learned a lot from your many posts.

---

### Post by oldfred on 2013-10-22
Thanks, but just about everything I know I learned from those before me.

---

### Post by jimford on 2013-10-22
I've looked at the dmesg logs, but nothing stands out, but I don't think a log gets written during the first incomplete boot.

As I stated, every first start up hangs during boot, and I have to power off, but the next proceeds OK from the Grub screen.

Thanks for the replies.

Jim

---

