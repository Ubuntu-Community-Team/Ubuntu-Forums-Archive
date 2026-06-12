---
title: "Using Gnome/Ubuntu 7.10 No GUI Add/Remove Programs and Admin menu with only 11entries"
date: 2008-01-27
forum: Desktop Environments
---

### Post by fiprojects on 2008-01-27
Something has gone wrong and I'm too new to Ubuntu/Gnome to figure it out.  I have Linux/Unix knowledge so I'd appreciate someone giving me some rough direction to fixing the problem.

Here goes:

Ubuntu 7.10 NO LONGER has 
- the Add/Remove Software that appears at the end of the Applications menu.
- System -> Administration now has 11entries total, excluding sypatic package management.

I've tried to perform a sudo bash but don't even get prompted for the password - I just get my ordinary vanilla shell though if I pass sudo some crap it does give me usage message.

Whats gone wrong?

---

### Post by fiprojects on 2008-01-27
Sorted!

I had been playing with samba and vmware with XP sitting on top and had performed a usermod on my user login.  The result of my usermod removed group 'admin' from my login which in effect stripped me of my add/remove and reduced the options on the system->administration menu.

How did I resolve?

I rebooted, put into safe mode which brought me straight to the root command line - then I used usermod again to modify my user account to include the admin group.

I don't want to share too much detail in case someone with lesser knowledge of me buggers up their system but I would hope there is enough information above to help someone forward if they should do the same thing i've done.

---

### Post by kbundies on 2008-02-17
I have my Applications/Administration menu completely gone. Is there a possibility to get it back?
Also under Applications/Other I have three instances of the same shortcut. Is there a way to clear this up?
Thank you very much

---

### Post by tmarthal on 2008-02-26
I had the same problem, but I was just installing and configuring cvs. Something happened to the groups that my default user / sudoer was part of. Adding the user back to the admin group didn't seem to allow me to get the admin menu options back.

I did notice that there was a /etc/group- (notice the dash) as well as an /etc/group file. The /etc/group- file had my sudoer user in many more groups. 

My solution was to log on into the recovery mode (as root) and just replaced the /etc/group file with the /etc/group- file (with the dash).

Nothing too complicated, but I bet that something is screwy.

*edit* the problem (I bet) is in the gnome 'Manage Groups' dialog. Did you (the original poster) use that to update some things, then reboot/logoff (in my case, 3 days later) and have problems?

---

