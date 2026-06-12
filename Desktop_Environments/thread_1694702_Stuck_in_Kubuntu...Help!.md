---
title: "Stuck in Kubuntu...Help!"
date: 2011-02-24
forum: Desktop Environments
---

### Post by Bre Ntt on 2011-02-24
I decided to try KDE (kubuntu), to see how it compared to GNOME. Nothing seemed to be working right in the KDE environment.  But now I can't get back to GNOME. 

I tried using synaptic to uninstall kubuntu-desktop, but somehow it is still throwing me into kubuntu when I log in. 

How do I get out of this place?

======
Update:

I looked at /etc/x11/default-display-manager

and it had 

/usr/sbin/gdm

I stupidly tried to change it to

/usr/sbin/kdm

Hoping to get the kdm splash screen that allows me to choose between GNOME and KDE (since gdm didn't seem to have that option)

I guess that wasn't a valid option because now the system won't even get past the Kubuntu load screen. Is there a way to get into a console so I can change defult-display-manager back to a valid option?

i tried to boot into safe mode, but the command line is all glitchy.

It asks me for the root password for maintenance, but as soon as I press a couple of keys of my password it says "login incorrect"

---

### Post by ankspo71 on 2011-02-25
Hi,
Whenever you get stuck like that without a desktop, pressing Ctrl+Alt+F2 can bring you to a console. But since you said "i tried to boot into safe mode, but the command line is all glitchy." I doubt this will be helpful.

So instead, use your Live CD and boot into it. You can then undo the change you made to the /etc/x11/default-display-manager file on your hard drive (not the one on the cd). Then reboot and everything should be back in order to boot back into Kubuntu.

When you get kubuntu on the hard drive booting again, follow the instructions on this link:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
The author created a single command to completely remove all of Kubuntu's packages, then it reinstalls all of Ubuntu's packages to ensure nothing is missing.

Btw, the package kubuntu-desktop is only a meta-package. Removing meta-packages doesn't remove the packages that it installed.

Hope this helps.

---

### Post by ankspo71 on 2011-02-25
I just noticed your avatar saying you are using an older version of *ubuntu. If that's still true, then [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) has links to instructions for 10.10 through 8.04 and [http://www.psychocats.net/ubuntu/puregnomehardy](http://www.psychocats.net/ubuntu/puregnomehardy) has links to instructions for "Hardy" though "Dapper"

---

### Post by wizard10000 on 2011-02-25
Simple.  Log out and when presented with a login screen select GNOME as your session instead of KDE.

Hope this helps -

edit:  Sorry - saw you didn't have a sessions option in GDM.  Never mind  ;)

---

### Post by Bre Ntt on 2011-04-05
Thanks for the help. Was able to do it through the Live CD and some KDE removal instructions I found, which are apparently necessarily hackish---weird state of affairs that getting rid of it requires such a hackish approach. It was so thoroughly screwed there wasn't any option to choose between gnome and kde. Don't know what happened, but all fixed now. Thanks again.

---

