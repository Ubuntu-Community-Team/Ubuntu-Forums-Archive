---
title: "Gnome Problem"
date: 2009-04-13
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-13
This Error was occured when ever i start my system.. how to recover this problem..
**There was an error starting the GNOME Settings Daemon.[B]**

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

---

### Post by CraigPaleo on 2009-04-13
Are you logging in as root?

---

### Post by suresh_vandiyur on 2009-04-13
> **CraigPaleo said:**
> Are you logging in as root?

No.. Am login with the normal user... i know root user can't login in the graphical mode... because the security...

---

### Post by CraigPaleo on 2009-04-13
There's a thread [here ]("http://ubuntuforums.org/showthread.php?t=577946")about similar problems.  I'd see if any of it applies to you, especially if you're having network difficulties, and if it does, try the remedies. This [blog]("http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/"), which is in the thread, might help.

---

### Post by suresh_vandiyur on 2009-04-13
> **CraigPaleo said:**
> There's a thread [here ]("http://ubuntuforums.org/showthread.php?t=577946")about similar problems.  I'd see if any of it applies to you, especially if you're having network difficulties, and if it does, try the remedies. This [blog]("http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/"), which is in the thread, might help.
 can u tell me your mail id.. i try after tell u... i think i need to change the interfaces file..ok.. **because i reboot the this error also occured network bus connection failed.. deactivate the etho and then nfs kernel deamon was started very slowly**....
 i had post the another thread also if u know see the thread and reply me.. plz...

---

### Post by CraigPaleo on 2009-04-13
> **suresh_vandiyur said:**
> can u tell me your mail id.. i try after tell u... i think i need to change the interfaces file..ok.. **because i reboot the this error also occured network bus connection failed.. deactivate the etho and then nfs kernel deamon was started very slowly**....
 i had post the another thread also if u know see the thread and reply me.. plz...

I don't know enough to walk you through anything. I only know how to search. You'd probably be better off waiting until someone more experienced comes along. I wish I could help.

---

### Post by CraigPaleo on 2009-04-21
Were you able to get it working?

---

### Post by suresh_vandiyur on 2009-06-02
try this solution, i found this after spending some time for googling....

add two line in file /etc/network/interfaces:
auto lo
iface lo inet loopback

and commenting out all entries with IPv6
then type sudo ifup lo on terminal, then reboot the system or gnome !

---

