---
title: "Gnome Crashes - No such user"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Del Pede on 2005-12-14
I've searched and searched, and tweaked settings for weeks now. I've finally thrown in the towel. I can not find a solution.

First the setup.
I have several computer running Ubuntu 5.04 and a few 5.10 at work. They are setup to get all the user accounts from a gentoo server, running NIS. Also the home directories are mounted out to the clients via NFS. 

Recently we started upgrading through the net, to Ubuntu 5.10, and then was when the problems started.
Some accounts/users can no longer use Gnome. When they log in, the gnome-panel crashes, and when i restarts it says it all ready found a panel runnig, and will quit. This continues forever, untill you kill X.

.xsessions in the users home's says:
"id: 'user': no such user"
and at other times, it says
"** (gnome-panel:7658): WARNING **: Failed to lock:  no locks available"

At this time, this affects two accounts. It's only the gnome panel that chrashes, and it only happends on Ubuntu 5.10 clients.

I've cleaned out all gnome config files in both accounts. I've deleted /tmp the users home dirs, and on the clients. I've installed nfs-common, as suggested in another post. I've cannot figure out, where the problems occurs - with the accounts or the clients. Other users can login easily on both 5.04 and 5.10. All user accounts "should" be grouped the same, and all clients have the same config in fstab, passwd, shadow, group and nsswitch.conf

Any suggestions would be greatly appreciated

- Del Pede

---

### Post by Del Pede on 2005-12-15
After going through /var/log/auth.log i found this

localhost gdm[6053]: pam_unix session opened for user lone by (uid=0"

That not the accounts UID, so somewhere, the client fails to get the appropriate UID from the NIS server it seems. The thing is, that some users are still able to login and work in Gnome, without anything crashes.

I'm having serious troubles finding out, what causes this

---

### Post by Del Pede on 2005-12-20
I'm still working on this. Scouring through /var/log/messages this popped up

>  Dec 19 10:18:13 localhost gconfd (lone-7417): starting (version 2.12.0), pid 7417
user 'lone'
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/etc
/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/usr
/share/gconf/local.mandatory" to a read-only configuration source at position 1
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readwrite:/ho
me/lone/.gconf" to a writable configuration source at position 2
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/etc
/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/usr
/share/gconf/local.defaults" to a read-only configuration source at position 4
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/usr
/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/usr
/share/gconf/debian.defaults" to a read-only configuration source at position 6
Dec 19 10:18:13 localhost gconfd (lone-7417): Resolved address "xml:readonly:/var
/lib/gconf/defaults" to a read-only configuration source at position 7
Dec 19 10:18:22 localhost gconfd (lone-7417): Resolved address "xml:readwrite:/ho
me/lone/.gconf" to a writable configuration source at position 0

Though that indicates a million things. Also, all users get the "no such user" error in there .xsession-errors. 

I've previously deleted all gnome settings/config files, but that never did anything. But when i just remove .gconf/apps/panel/objects/menu_bar_screen0/%gconf.xml THEN users can log in to Gnome, without the panel crashing, but they won't have any menubar, since that is what i removed. When they add the menu to the panel again, panel crashes. If they press alt+f2 to try and run a program, the panel crashes.

All this is ONLY affecting some users, and ONLY on Ubuntu 5.10 machines.
This indicates to me, that something is messed up in the Ubuntu menu. But why it only affects some users, i have no idea

---

